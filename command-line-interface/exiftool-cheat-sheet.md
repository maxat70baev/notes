# Useful links:
[EXIF tag names]("http://www.sno.phy.queensu.ca/~phil/exiftool/TagNames/EXIF.html")
[Shortcuts tags documentation]("http://www.sno.phy.queensu.ca/~phil/exiftool/TagNames/Shortcuts.html")
[ExifTool FAQ]("http://www.sno.phy.queensu.ca/~phil/exiftool/faq.html")

# Examples:
`exiftool -EXIF:dateTimeOriginal="YYYY:mm:dd HH:MM:SS" a.jpg` - set date/time when original image was taken;
`exiftool -DateTimeOriginal-='0:0:0 1:30:0' dir` - adjust original date/time of all images in directory "dir" by subtracting one hour and 30 minutes (this is equivalent to `-DateTimeOriginal-=1.5`);
`exiftool '-FileModifyDate<DateTimeOriginal' dir` - use the original date from the meta information to set the same file's filesystem modification date for all images in a directory;
`exiftool -delete_original dir` - delete "_original" backups in directory;