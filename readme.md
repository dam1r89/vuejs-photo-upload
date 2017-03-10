Photo upload component, not trying to be "reusable component". It works on its own or you can use it as a starting point.

![Photo Upload](https://github.com/dam1r89/vuejs-photo-upload/raw/master/animation.gif)

Example

```javascript
Vue.component('photo-upload', require('./components/PhotoUpload.vue'));
```

and

```html
<photo-upload @input="handleFileUpload" :value="value"></photo-upload>
```

Value is current image preview (if image is already uploaded)

Example how to upload photo, or other way is to serialize file with base64.

```javascript
uploadLogo(file){
    let form = new FormData();
    form.append('photo', file);

	// or this.$http
    axios.post(`/api/upload`, form).then(res => {
		
    }, res => {

    });
},
```

Ideas from [here](http://stackoverflow.com/questions/25092981/drag-drop-images-input-file-and-preview-before-upload) and [here](https://css-tricks.com/drag-and-drop-file-uploading).

Json file upload [here](http://stackoverflow.com/questions/4083702/posting-a-file-and-data-to-restful-webservice-as-json)

Drag and drop [reference](https://developer.mozilla.org/en-US/docs/Web/Events/dragenter) and [support](http://caniuse.com/#feat=dragndrop) 
