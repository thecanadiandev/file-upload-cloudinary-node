# README

make sure, we have a cloudinary account, and add

```
CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=
```

and also create a folder within the same, and use that name while uploading.

```js
const uploadProductImage = async (req, res) => {
  const result = await cloudinary.uploader.upload(
    req.files.image.tempFilePath,
    {
      use_filename: true,
      folder: 'file-uploads',
    }
  );
  fs.unlinkSync(req.files.image.tempFilePath);
  return res.status(StatusCodes.OK).json({ image: { src: result.secure_url } });
};
```
