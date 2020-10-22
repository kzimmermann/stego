# A steganography tool to conceal data within JPG images.

`stego` is a steganography script designed to hide data inside innocent-looking JPG images, where doing so does not alter either the way the image looks (image data is completely preserved) or the integrity of the data (hidden data can be obtained exactly like it was inserted).

You can use `stego` to bypass some sorts of content filters, where some content-types like executables, archives or unknown extensions might be blocked, but images are allowed through without questions.

A word of warning: `stego` does **not** perform any sort of encryption of the hidden data. If the data you're attempting to hide is by any means sensitive, **encrypt it before using stego.**

## The workings

`stego` makes use of a clever, but now well-known trick where a zip file is "glued" to the end of a JPG, causing the file to remain as a normal image, but also become a valid zip file that can be opened with any archiver as long as the extension is changed to `zip`. For the best effect, choose an image that is large in comparison to the hidden data, so that it will look the most like an innocent image.

Please keep in mind that some image uploading utilities or services, like WhatsApp, perform some compression and resizing to the image, which causes the "non-image" bytes to be shaved off the file and you lose the hidden data. If the image is left untouched, stego works well.

## Usage

    stego IMAGE.jpg FILE1 FILE2 FILE3... FILEN

Where `IMAGE.jpg` is the image that will conceal the `FILEs`.

Again, `stego` is not an encryption tool: if your files are sensitive, encrypt them *before* feeding them to `stego`.
