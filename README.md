# DEPRECATED
android-multiple-image-picker is deprecated. No more development will be taking place. Most file managers and gallaries now support ```Intent.EXTRA_ALLOW_MULTIPLE``` Thanks for all your support!

# Mutiple Image Picker

Recently I got frustrated opening an intent to select multiple photos and also with a camera. Therefore I to make it myself and so other people don't have to reinvent the wheel here it is.


## Usage

```java
private static final RESULT_CODE_PICKER_IMAGES = 9000;


Intent intent = new Intent(this, SmartImagePicker.class);
startActivityForResult(intent, RESULT_CODE_PICKER_IMAGES);


@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
    switch (requestCode){
        case RESULT_CODE_PICKER_IMAGES:
            if(resultCode == Activity.RESULT_OK){
                Parcelable[] parcelableUris = data.getParcelableArrayExtra(ImagePickerActivity.TAG_IMAGE_URI);

                //Java doesn't allow array casting, this is a little hack
                Uri[] uris = new Uri[parcelableUris.length];
                System.arraycopy(parcelableUris, 0, uris, 0, parcelableUris.length);

                //Do something with the uris array
            }
            break;

        default:
            super.onActivityResult(requestCode, resultCode, data);
            break;
    }
}
```

## Result

<img src="https://raw.githubusercontent.com/giljulio/ImagePicker/master/example/src/main/res/drawable/screenshot1.png" width="200px" style="margin: 5px;" /><img src="https://raw.githubusercontent.com/giljulio/ImagePicker/master/example/src/main/res/drawable/screenshot2.png" width="200px" style="margin: 5px;" /><img src="https://raw.githubusercontent.com/giljulio/ImagePicker/master/example/src/main/res/drawable/screenshot3.png" width="200px" style="margin: 5px;" />
