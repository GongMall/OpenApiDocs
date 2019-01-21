### 基于App嵌入合同的一些配置

---

**简要描述：**

* 业务背景

  电签业务增加了上传身份证功能，由于客户技术对接时，经常出现身份证不能上传的问题，特推出一个简单的解决方案。

**基于App嵌套电签上传身份证出现不能点击问题解决方案：**

```
- 问题描述 

     点击H5中 input type="file" 标签，不能打开android资源管理器，因为 android webview 由于考虑安全原因屏蔽了 input type="file" 这个功能，需要做如下配置方可使用。

1、配置：
public ValueCallback<Uri[]> uploadMessage;
private final static int FILECHOOSER_RESULTCODE = 2;
private ValueCallback<Uri> mUploadMessage;
public static final int REQUEST_SELECT_FILE = 100;
private Uri imageUri;

2、重写onActivityResult
    public void onActivityResult(int requestCode, int resultCode, Intent intent) {
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
        if (requestCode == REQUEST_SELECT_FILE) {
            if (uploadMessage == null)
                return;
            uploadMessage.onReceiveValue(WebChromeClient.FileChooserParams.parseResult(resultCode, intent));
            uploadMessage = null;
        }
    } else if (requestCode == FILECHOOSER_RESULTCODE) {
        if (null == mUploadMessage)
            return;
        // Use MainActivity.RESULT_OK if you're implementing WebView inside Fragment
        // Use RESULT_OK only if you're implementing WebView inside an Activity
        Uri result = intent == null || resultCode != MainActivity.RESULT_OK ? null : intent.getData();
        mUploadMessage.onReceiveValue(result);
        mUploadMessage = null;
    } else
        Toast.makeText(getBaseContext(), "Failed to Upload Image", Toast.LENGTH_LONG).show();
}

3、添加webview的WebChromeClient配置
    private WebChromeClient webChromeClient = new WebChromeClient() {
    protected void openFileChooser(ValueCallback uploadMsg, String acceptType) {
        mUploadMessage = uploadMsg;
        take();
    }

    @TargetApi(Build.VERSION_CODES.LOLLIPOP)
    public boolean onShowFileChooser(WebView mWebView, ValueCallback<Uri[]> filePathCallback, WebChromeClient.FileChooserParams fileChooserParams) {
        if (uploadMessage != null) {
            uploadMessage.onReceiveValue(null);
            uploadMessage = null;
        }
        uploadMessage = filePathCallback;
        take();
        return true;
    }

    //For Android 4.1 only
    protected void openFileChooser(ValueCallback<Uri> uploadMsg, String acceptType, String capture) {
        mUploadMessage = uploadMsg;
        take();
    }

    protected void openFileChooser(ValueCallback<Uri> uploadMsg) {
        mUploadMessage = uploadMsg;
        take();
    }
};

private void take() {
    File imageStorageDir = new File(Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_PICTURES), "MyApp");
    // Create the storage directory if it does not exist
    if (!imageStorageDir.exists()) {
        imageStorageDir.mkdirs();
    }
    File file = new File(imageStorageDir + File.separator + "IMG_" + String.valueOf(System.currentTimeMillis()) + ".jpg");
    imageUri = Uri.fromFile(file);

    final List<Intent> cameraIntents = new ArrayList<Intent>();
    final Intent captureIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
    final PackageManager packageManager = getPackageManager();
    final List<ResolveInfo> listCam = packageManager.queryIntentActivities(captureIntent, 0);
    for (ResolveInfo res : listCam) {
        final String packageName = res.activityInfo.packageName;
        final Intent i = new Intent(captureIntent);
        i.setComponent(new ComponentName(res.activityInfo.packageName, res.activityInfo.name));
        i.setPackage(packageName);
        i.putExtra(MediaStore.EXTRA_OUTPUT, imageUri);
        cameraIntents.add(i);

    }
    Intent i = new Intent(Intent.ACTION_GET_CONTENT);
    i.addCategory(Intent.CATEGORY_OPENABLE);
    i.setType("image/*");
    Intent chooserIntent = Intent.createChooser(i, "Image Chooser");
    chooserIntent.putExtra(Intent.EXTRA_INITIAL_INTENTS, cameraIntents.toArray(new Parcelable[]{}));
    MainActivity.this.startActivityForResult(chooserIntent, FILECHOOSER_RESULTCODE);
}

```

**合同不能正常显示问题请做如下配置：**

```
- 问题描述 

     webview嵌入h5合同页面会产生一些兼容问题，需要做如下配置。

解决方法：
WebSettings webSettings = webView.getSettings();
webSettings.setJavaScriptEnabled(true);//允许使用js
// 解决兼容显示问题
webSettings.setDomStorageEnabled(true);
webSettings.setSupportZoom(true);
webSettings.setBuiltInZoomControls(true);
webSettings.setUseWideViewPort(true);
webSettings.setLoadWithOverviewMode(true);
webSettings.setLayoutAlgorithm(WebSettings.LayoutAlgorithm.SINGLE_COLUMN);
```

**ios app选择图片的问题：**

```
- 问题描述
    关于ios app选择图片完成后页面会返回问题：

解决方法：      
loadRequest需要在在viewDidLoad内调用
```



