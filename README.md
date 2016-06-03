# i18next_test

This is the demo of the usage of i18next for website by pure javascript and html

the source js files are all from http://i18next.com/

* test_v1.html

  use i18next v1.11.x http://i18next.github.io/i18next/
  
  ```js
  i18n.init({
      debug: true,
      lng: "zh_TW",
      resGetPath: 'resources/__ns__-__lng__.json'
  }, function () {
  	  //callback
  });
  ```
  
* test.html

  use i18next v3.1.0 https://github.com/i18next/i18next
  
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
  As the offical website said, the new version does not come with backend, cache and user language detection built in. 
  so we need to include the backend files to load the resources language files, see https://github.com/i18next/i18next-xhr-backend
  
  the default prefix, suffix of interpolation rule is "{{" and "}}", the example is just shown how to use "__" as prefix and suffix 
