# i18next_test

This is the example of i18next for browsers ny using pure javascript and html

more info: http://i18next.com/

###init and load resource file###

the default prefix, suffix of interpolation rule is "{{" and "}}", the example is just shown how to use "__" as prefix and suffix

* **test_v1.html** - use i18next v1.11.x http://i18next.github.io/i18next/
  
  ```js
  i18n.init({
      debug: true,
      lng: "zh_TW",
      resGetPath: 'resources/__ns__-__lng__.json'
  }, function () {
  	  //callback
  });
  ```
  
* **test.html** - use i18next v3.1.0 https://github.com/i18next/i18next
 
 As the offical website said, the new version does not come with backend, cache and user language detection built in. 
 so we need to include the backend files to load the resources language files, see https://github.com/i18next/i18next-xhr-backend
  
  ```js
  i18next.use(i18nextXHRBackend)
     .init({
          debug: true,
          lng: "zh_TW",
          backend: {
              loadPath: 'resources/__ns__-__lng__.json'
          },
          interpolation: {
          	prefix: '__',
          	suffix: '__',
          	unescapePrefix: '~'
          }
      }, function () {
          //callback
	});
  ```

###reload resource file###

* **test.html** - use i18next v3.1.0 https://github.com/i18next/i18next
 
 Sometimes you will need to reload the resource file (if the resource file is being updated very often, you don't want to init again but can reload it dynamically.) 

 Actually this is being discussed at i18next github site https://github.com/i18next/i18next/issues/707.

 Here is just a sample for browser, try modifying the resource file before clicking the button.
 
 ```js
 var nss = i18next.options.ns;
 for (var i = 0; i < nss.length; i++) {
	var ns = nss[i];
	backendConnector.read(lng, ns, 'read', null, null, function(err, data){
		if (err) {
			console.warn('loading namespace '+ ns + ' for language ' + lng + ' failed,' + err );
		}
		else if (!err && data) {
			console.log('loaded namespace '+ ns + ' for language ' + lng);
			console.log(data)
			backendConnector.loaded(lng+'|'+ns, err, data);
		}
	});
 }
 ```
