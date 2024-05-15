### Downloading Images

If you have a URL, downloading an image can be done like this.

``` java
URL url = new URL("http://...);
Image image = ImageIO.read(url)
 ```

If you want to scale the image while keeping the same aspect ration you can call

``` java 
Image scaledImage = image.getScaledInstance(200, -1, Image.SCALE_DEFAULT);
```

This will scale it to a width of 200 pixels and setting the height to the same proportion.

Once you have the scaled image, you can display it in a `JLabel`.

``` java 
JLabel label = new JLabel();
ImageIcon imageIcon = new ImageIcon(scaledImage);
label.setIcon(imageIcon);
```