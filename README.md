This is port of https://github.com/18446744073709551615/android-file-chooser-dialog to Xamarin Android
with better design and an easy usage using async and enum.

Xamarin android file and folder chooser/picker dialog
===========================

Android file chooser, a dialog to pick a filename.

The code is taken from
http://www.scorchworks.com/Blog/simple-file-dialog-for-android-applications/
with a few added features and bug fixes.

What has changed: I needed ability to go to the root directory, but the original code did not permit
going above the sdcard mount point, and if you used a non-default start folder not on sdcard,
the code crashed in the root directory. This has been fixed.

Usage example
-------------

    public void OpenFolderDialog() {
        //Create FolderOpenDialog
         SimpleFileDialog fileDialog = new SimpleFileDialog(this, SimpleFileDialog.FileSelectionMode.FolderChoose);
         string path = await fileDialog.GetFileOrDirectoryAsync(Android.OS.Environment.ExternalStorageDirectory.AbsolutePath);
         if (!String.IsNullOrEmpty(path))
         {
			//Use path
         }
    }

And remember

    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
	
Screenshot:

![Alt text](screenshot.png?raw=true "Screenshot")

Dialog modes
------------

    "FileSelectionMode.FileOpen" -- open an existing file
    "FileSelectionMode.FileSave" -- save to a file
    "FileSelectionMode.FolderChoose" -- choose a folder
    "FileSelectionMode.FileOpenRoot" -- open an existing file, can cd .. from the starting directory
    "FileSelectionMode.FileSaveRoot" -- save to a file, can cd .. from the starting directory
    "FileSelectionMode.FolderChooseRoot" -- choose a folder, can cd .. from the starting directory

