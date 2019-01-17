### 基于App嵌入合同的一些配置
---

**简要描述：** 

- 业务背景

    电签电业增加了上传身份证功能，由于客户技术对接时，经常出现身份证不能上传的问题，特推出一个简单的解决方案。


**基于App嵌套电签上传身份证出现不能点击问题解决方案：** 
```
- 问题描述 

     点击H5中 input type="file" 标签，不能打开android资源管理器，因为 android webview 由于考虑安全原因屏蔽了 input type="file" 这个功能，需要做如下配置方可使用。

1、配置：
public ValueCallback<Uri[]> uploadMessage;
private final static int FILECHOOSER_RESULTCODE = 2;
private ValueCallback<Uri> mUploadMessage;
public static final int REQUEST_SELECT_FILE = 100;

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
        Intent i = new Intent(Intent.ACTION_GET_CONTENT);
        i.addCategory(Intent.CATEGORY_OPENABLE);
        i.setType("image/*");
        startActivityForResult(Intent.createChooser(i, "File Browser"), FILECHOOSER_RESULTCODE);
    }

    @TargetApi(Build.VERSION_CODES.LOLLIPOP)
    public boolean onShowFileChooser(WebView mWebView, ValueCallback<Uri[]> filePathCallback, WebChromeClient.FileChooserParams fileChooserParams) {
        if (uploadMessage != null) {
            uploadMessage.onReceiveValue(null);
            uploadMessage = null;
        }
        uploadMessage = filePathCallback;
        Intent intent = fileChooserParams.createIntent();
        try {
            startActivityForResult(intent, REQUEST_SELECT_FILE);
        } catch (ActivityNotFoundException e) {
            uploadMessage = null;
            Toast.makeText(getBaseContext(), "Cannot Open File Chooser", Toast.LENGTH_LONG).show();
            return false;
        }
        return true;
    }

    //For Android 4.1 only
    protected void openFileChooser(ValueCallback<Uri> uploadMsg, String acceptType, String capture) {
        mUploadMessage = uploadMsg;
        Intent intent = new Intent(Intent.ACTION_GET_CONTENT);
        intent.addCategory(Intent.CATEGORY_OPENABLE);
        intent.setType("image/*");
        startActivityForResult(Intent.createChooser(intent, "File Browser"), FILECHOOSER_RESULTCODE);
    }

    protected void openFileChooser(ValueCallback<Uri> uploadMsg) {
        mUploadMessage = uploadMsg;
        Intent i = new Intent(Intent.ACTION_GET_CONTENT);
        i.addCategory(Intent.CATEGORY_OPENABLE);
        i.setType("image/*");
        startActivityForResult(Intent.createChooser(i, "File Chooser"), FILECHOOSER_RESULTCODE);
    }
};

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


