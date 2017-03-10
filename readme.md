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
handleFileUpload(file){
    let form = new FormData();
    form.append('photo', file);

	// or this.$http
    axios.post(`/api/upload`, form).then(res => {
		
    }, res => {

    });
},
```

