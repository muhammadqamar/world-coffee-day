# PUBLIC Landing Pages

## Project setup
To run the project:

Install the dependencies
```
npm i
```

Run in Dev mode
```
npm start
```

Build the page*
```
npm run build
```

Serve the project from dist folder
```
npm run serve
```

***NOTICE**

Client uses a specific platform thus more changes need to be done in order to be ready for them.

- All external javascript libraries (sliders, etc.) needs to be inlined in their own <script> tag at the beginning of <head> tag. By inline we mean that we copy-paste the contents of library's file to an empty <script> tag. It's important to notice that we must not include it as srcipt tag with `src` attribute or pass it through a bundler like webpack / parcel.
- Our script should be written and inserted into a <script> tag right before the closing of body tag. Keep in mind we can't use window event listeners (for example 'DOMContentLoaded'), that's why we add it at the end of our DOM Content. That way we ensure that we have the markup ready to reference it in our scripts.
- CSS must also be inlined into it's own <style> tag in <head>. CSS can be generated from (pre|post)processors and then inlined.
- We need to alter the url of each asset. Parcel bundler uses relative urls for the final build assuming it will run on it's own server. If we reference any asset (image, js, html) thoughout our project we must change it's relative path to an absolute path. For example we replace all `src="/` with `src="./` for images/videos and all `url(` with `url(./` for CSS rules.
- Since there is a change to name a CSS class the same as their CMS does it's a good idea to either keep our CSS under an umbrella class for example `.holy .container`, `.holy .header` etc. or even better to add a prefix in our classes. ie. `.holy-container`, `.holy-header` etc. That way we don't mess with specificity.
