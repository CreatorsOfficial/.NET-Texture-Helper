# .NET-Texture-Helper
.NET Texture Helper is a C# library used for texture format encoding and decoding used in Unity 3d

For this purpose Unity libraries has been used and for making thing easier they are used by another native library

Here are some examples on how to use this Library

#Getting a Texture2D from a png
We can load the texture2D from an image/png stored in a directory by using the following code

    ```csharp
        public void LoadTexture()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            lib.Texture = rlib.loadfromDirectory("C:/hi.png");
        }
    ```
#Loading a Texture2D from Bytes
if you have the bytes of an image (which you can also get through File.ReadAllBytes(string path);
or from some other way and they are from some png or jpg or some other image format but remind that they should not be some raw texture like RGBA32 or ETC_RGB32A8)
then we can loas it by using the code below
    ```csharp
        public void LoadTextureFromBytes()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            byte[] bytes = File.ReadAllBytes("C:/hi.png");
            lib.Texture = rlib.LoadFromImageBytes(bytes);
        }
    ```
#Loading a Texture2D from raw texture bytes
This is basically a conversion of the raw texture from its raw format to default RGBA32 format
For this purpose you get the bytes of raw texture from either your directory or some other source then use the following code to convert it to standard Texture2D
    ```csharp
        public void LoadRawTextureFromBytes()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            byte[] bytes = File.ReadAllBytes("C:/myrawtex.tex");
            lib.Texture = rlib.LoadFromRawImageBytes(bytes);
        }
    ```
#Changing Texture Format
One you have loaded a texture2D you have the format RGBA32 by default
You dont want the RGBA32 for some purpose and want to use some other format like RG16,ARGB32 and so on
Then you can convert the texture to some other texture format by this code
    ```csharp
        public void changeTextureFormat()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            lib.Texture = rlib.loadfromDirectory("C:/my.png");
            NetLibrary.revertLib revertClass = new NetLibrary.revertLib();
            revertClass = rlib.revertForm(lib.Texture, UnityEngine.TextureFormat.Alpha8);
            lib.Texture = revertClass.revertedTex2D;
        }
    ```
#Get the png from the Texture2D
For getting the png from the texture2D you have computed
you can use the following code
    ```csharp
        public void GetPng()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            lib.Texture = rlib.loadfromDirectory("C:/my.png");
            NetLibrary.revertLib revertClass = new NetLibrary.revertLib();
            revertClass = rlib.revertForm(lib.Texture, UnityEngine.TextureFormat.Alpha8);
            lib.Texture = revertClass.revertedTex2D;
            byte[] mypngBytes = rlib.getPngBytes(lib, lib.Texture);
        }
    ```
#Get the Raw texture bytes from Texture2D
For getting the raw texture bytes from the texture2D with raw TextureFormat
You can use the code below
    ```csharp
        public void GetRawTex()
        {
            NetLibrary lib = new NetLibrary();
            reversionLib rlib = new reversionLib();
            lib.Texture = rlib.loadfromDirectory("C:/my.png");
            NetLibrary.revertLib revertClass = new NetLibrary.revertLib();
            revertClass = rlib.revertForm(lib.Texture, UnityEngine.TextureFormat.Alpha8);
            lib.Texture = revertClass.revertedTex2D;
            byte[] rawBytes = rlib.getRawBytes(lib, lib.Texture);
        }
    ```
