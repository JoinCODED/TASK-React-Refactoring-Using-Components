### Frontend

Refactor your code to use components.

#### Setup

1. If you're not using [Google Chrome](https://www.google.com/chrome/?brand=CHBD&gclid=CjwKCAjwh472BRAGEiwAvHVfGlGs5LCRtT3uFIpRZ8A2rPZ_BxrTiEFfDSm21fn1EBKD0GkIHC3zThoC5mIQAvD_BwE&gclsrc=aw.ds), it's time to use it!
2. Download the [React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) extension.
3. Go to your website (you might need to quit and open it again), open `Inspect` and make sure two tabs are added `components` and `profile`.

#### Home Component

1. Create a `components` folder inside `src`.
2. Create a new file and name it `Home.js`.
3. Create a function that represents your component.
4. Move the relevant JSX (website title, description and shop image)and all relevant code from `App.js` into the new component.
5. Export your component and import it in `App.js`.
6. Use the new component in `App.js`.
7. Check your website to make sure your code is correct, everything should look exactly the same.
8. Open the React Dev Tools and click on `component`. Your new component `Home` should be under `App`.

#### Product List Component

1. Create a new file and name it according to your shop's theme, make sure that the name starts with a capital letter. We'll call ours `ProductList`.
2. Create a function that represents your component and export it at the end of the file.
3. Move the relevant JSX and all relevant code from `App.js` into the new component.
4. Import your data file.
5. Import your component in `App.js` and render it.
6. Check your website to make sure your code is correct, everything should look exactly the same.
7. Open the React Dev Tools and click on `component`. Your new component should be under `App`.

#### Product Item Component

1. Create a new file for your product item component and name it according to your shop's theme, make sure that the name starts with a capital letter. We'll call ours `ProductItem`.
2. Follow the steps above to create a component.
3. Move the relevant JSX from the list component to the new component.
4. In your `ProductList` component, import your `ProductItem` component.
5. In the `map` method, render the `ProductItem` component and pass your product as a prop.
6. In your `ProductItem` component, pass `props` as your function's argument.
7. In your `products.js` file, add an `id` field to all your products.
8. Pass a `key` as a prop to the `ProductItem` component. The value of the key should be the product's ID.
9. Check your website to make sure your code is correct, everything should look exactly the same.
10. Open the React Dev Tools and click on `component`. Your new component should be under `App`.
