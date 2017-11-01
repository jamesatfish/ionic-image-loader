[![npm](https://img.shields.io/npm/l/ionic-image-loader.svg)](https://www.npmjs.com/package/ionic-image-loader/)
[![npm](https://img.shields.io/npm/dt/ionic-image-loader.svg)](https://www.npmjs.com/package/ionic-image-loader)
[![npm](https://img.shields.io/npm/dm/ionic-image-loader.svg)](https://www.npmjs.com/package/ionic-image-loader)

# Ionic Attributed Image Loader
**Ionic** Module that loads images in a native background thread and caches them for later use. Uses `cordova-plugin-file` and `cordova-plugin-file-transfer` via [`ionic-native`](https://github.com/driftyco/ionic-native) wrappers.

#This is a forked module*
This module has been forked from the original ionic-image-loader module by Zyra Media.  Please refer to the original module page (https://github.com/zyramedia) for full documentation.

## Features
- Enhances the Zyra Media ionic-image-loader by providing the ability to pass through image attributes when generating the HTML <img> tags.


## Installation

#### 1. Install the NPM Package
```
npm install --save ionic-image-loader
```

#### 2. Install Required Plugins
```
npm i --save @ionic-native/file
ionic cordova plugin add cordova-plugin-file

npm i --save @ionic-native/file-transfer
ionic cordova plugin add cordova-plugin-file-transfer
```

#### 3. Import `IonicAttributedImageLoader` module

**Add `IonicAttributedImageLoader.forRoot()` in your app's root module**
```typescript
import { IonicAttributedImageLoader } from 'ionic-attributed-image-loader';

// import the module
@NgModule({
  ...
  imports: [
    IonicAttributedImageLoader.forRoot()
  ]
})
export class AppModule {}
```

**Then add `IonicAttributedImageLoader` in your child/shared module(s)**
```typescript
import { IonicAttributedImageLoader } from 'ionic-attributed-image-loader';

@NgModule({
  ...
  imports: [
    IonicAttributedImageLoader
  ]
})
export class SharedModule {}
```

# Usage

## Basic Usage
By default, the module sets the image as the background of the `<img-loader>` element. If you want the module to use the image as an `<img>` tag inside the `<img-loader>` elemen, just add `useImg` attribute as shown below:
```html
<img-loader src="https://path.to/my/image.jpg" useImg></img-loader>
```

You can also listen to the load event to be notified when the image has been loaded:
```html
<img-loader src="path/to/image" (load)="onImageLoad($event)></img-loader>
```
```typescript
import { ImgLoader } from 'ionic-image-loader';


## Advanced Usage
The `<img-loader>` component takes many attributes that allows you to customize the image. You can use the following table as a reference:

| Attribute Name | Type | Description | Default Value |
| --- | --- | --- | --- |
| src | string | The image URL | N/A |
| fallback | string | Fallback image url to load in case the original image fails to load | N/A |
| spinner | boolean | Show a spinner while the image loads | true |
| useImg | boolean | Use `<img>` tag to display the image in | false |
| width | string | The width of the image. This is ignored if `useImg` is set to `true`. | 100% |
| height | string | The height of the image. This is ignored if `useImg` is set to `true`. | 100% |
| display | string | Sets the `display` CSS property of the `<img-loader>` element. This is ignored if `useImg` is set to `true`. | block |
| backgroundSize | string | Sets the `background-size` CSS property of the `<img-loader>` element. This is ignored if `useImg` is set to `true`. | contain |
| backgroundRepeat | string | Sets the `background-repeat` CSS property of the `<img-loader>` element. This is ignored if `useImg` is set to `true`. | no-repeat |
| fallbackAsPlaceholder | boolean | Use fallback as a placeholder until the image loads. | false |
| imgAttributes | ImageAttribute[] | An array of ImageAttribute objects (element, value).  If `useImg == true`, this array will be iterated and each object added as an attribute to the generated `<img>` HTML element. | []] |


**Note:** The default values can be changed using the [global configuration](https://github.com/zyramedia/ionic-image-loader#global-configuration) feature.



# Passing HTML / CSS Attributes to a generated image

When using ImageLoader to generate an `<img>` element it may be desirable for the generated element to include additional attributes to provide styling or interaction qualities.  The optional `imgAttributes` value can be used to provide such additional attributes which will be included in the generated `<img>` element in the DOM.

Usage:

1. Include the ImageAttribute model in your .ts
```typescript
import { ImageAttribute } from 'ionic-image-loader'
```

2. Generate an array of ImageAttribute objects
```typescript
var imageAttributes: ImageAttribute[] = [];
imageAttributes.push({
  element: 'class',
  value: 'circle-photo'
})
```

3. Include the `imgAttributes` element in the `img-loader` element of your HTML
```html
 <img-loader [src]="..." useImg [imgAttributes]="imageAttributes"> </img-loader>
```

4. The generated `<img>` tag will be rendered with the specified attributes
```html
  <img src="..." class="circle-photo">
```

<br><br>
## Contribution
- **Having an issue**? or looking for support? [Open an issue](https://github.com/zyra/ionic-image-loader/issues/new) and we will get you the help you need.
- Got a **new feature or a bug fix**? Fork the repo, make your changes, and submit a pull request.

## Support this project
If you find this project useful, please star the repo to let people know that it's reliable. Also, share it with friends and colleagues that might find this useful as well. Thank you :smile:
