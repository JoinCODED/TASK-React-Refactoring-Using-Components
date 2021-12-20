#### Home Component

At this point, all of our code is in `App.js`. But what will happen when our website becomes bigger? Basically, we will split the code in `App.js` to many components.

1. First, we will create a folder called `components`. This is where we will place all our components except `App.js`.

2. Now in `components`, we will create a file called `Home.js`.

3. In `Home.js`, we will create a function -which is our component- called `Home`. The component must start with a capital letter, otherwise it will cause you issues.

 ```jsx
const Home = () => {};
 ```

4. The return value of this function is the JSX that will be rendered on the screen when `Home` is called. For now let's add any message to it.

 ```jsx
const Home = () => {
  return <h1>I'm the Home component!</h1>;
};
 ```

5. To use this component in `App.js`, we will need to import it. And you can't import something if it's not exported.

 ```jsx
const Home = () => {
  return <h1>I'm the Home component!</h1>;
};
export default Home;
 ```

6. In `App.js`, import `Home`. Regarding the path, for `App.js` to reach `Home.js`, it has to go inside `components` folder and to `Home.js` to import it. Since `App.js` and `components` are in the same directory the path will start with `./` followed by the `components` which is the directory we want to go to followed by `Home` which is the file we want to reach into.

 ```jsx
// Components
import Home from "./components/Home";
 ```
7. Now how can we render `Home`? To render a component, we will wrap it in a tag.

 ```jsx
return (
    <div className="body">
        <div>...</div>
        <Home />
    <div>
)
 ```

8. Let's move our title, description and image to the `Home` component.

 ```jsx
// Styling
const Home = () => {
  return (
    <div>
      <h1 className="text">Cookies and Beyond</h1>
      <h4 className="text">Where cookie maniacs gather</h4>
      <img
        alt="cookie shop"
        src="https://i.pinimg.com/originals/8f/cf/71/8fcf719bce331fe39d7e31ebf07349f3.jpg"
        className="shopImage"
      />
    </div>
  );
};
 ```

#### Product List Component
Let's also create a component for our list of cookies.

1. Now in `components`, we will create a file called `CookieList.js`.

2. Then, we will create our function, `CookieList`.

 ```jsx
const CookieList = () => {
 return <h1>I'm the CookieList component!</h1>;
};
export default CookieList;
  ```

3. In `App.js`, import `CookieList`.

 ```jsx
// Components
import CookieList from "./components/CookieList";
import Home from "./components/Home";
 ```
4. Render it under `Home`.

 ```jsx
  return (
    <div className="body">
        <div>...</div>
        <Home />
        <CookieList />
    <div>
  )
 ```

5. Now let's move our cookie list to the `CookieList` component. And don't forget to import your `cookies` data.

 ```jsx
 // Data
 import cookies from "../cookies";
 
 const CookieList = () => {
   const cookieList = cookies.map((cookie) => (
     <div className="product"}>
       <img className="productImage" alt={cookie.name} src={cookie.image} />
       <p className="text">{cookie.name}</p>
       <p className="text">{cookie.price} KD</p>
     </div>
   ));
   return <div className="list">{cookieList}</div>;
 };
 ```

#### Product Item Component

1. In `components`, we will create a file called `CookieItem.js`.

2. Then, we will create our component function `CookieItem`. And let's move in the `cookie` JSX from `CookieList.js`.

 ```jsx
 const CookieItem = (props) => {
   const cookie = props.cookie;
   return (
     <div className="product"}>
       <img className="cookie-image" alt={cookie.name} src={cookie.image} />
       <p className="text">{cookie.name}</p>
       <p className="text">{cookie.price} KD</p>
     </div>
   );
 };

 export default CookieItem;
 ```

3. In `CookieList.js`, import `CookieItem`.

 ```jsx
 // Components
 import CookieItem from "./CookieItem";
 ```
4. We will render `CookieItem` in the map method.

 ```jsx
 const cookieList = cookies.map((cookie) => <CookieItem cookie={cookie} />);
 ```
Let's open the console, we got a warning ladies and gentlemen:

 ```
 Warning: Each child in a list should have a unique "key" prop.
 ```

5. Now technically speaking, we can ignore warnings, but this warning will give us issues later on. Basically, when we save JSX elements in an array, `React` needs to have a unique `key` for every element. This key must be added to the parent tag as an attribute, but what will the unique value be?

 ```jsx
 const cookieList = cookiesData.map((cookie) => (
   <CookieItem cookie={cookie} key={} />
 ));
 ```
6. Let's take a look at the `data` array, the name and image are unique values. But we need something more reliable, so we will add a field called `id` which is a unique that will never be repeated.
 
 ```jsx
 const cookies = [
   {
     id: 1,
     name: "Chocolate Chip Cookie",
     price: 10,
     image:
       "https://joyfoodsunshine.com/wp-content/uploads/2016/01/best-chocolate-chip-cookies-recipe-ever-no-chilling-1.jpg",
   },
   {
     id: 2,
     name: "Adorable Cookie",
     price: 15,
     image:
       "https://i.pinimg.com/originals/f6/3e/2a/f63e2a1cd0c7d3c0ab9cd277d3f32050.jpg",
   },
   {
     id: 3,
     name: "Katakeet Cookie",
     price: 7,
     image:
       "https://imagesvc.meredithcorp.io/v3/mm/image?url=https%3A%2F%2Fassets.marthastewart.com%2Fstyles%2Fwmax-750%2Fd34%2Feaster-chick-egg-cookies-102921707%2Feaster-chick-egg-cookies-102921707_horiz.jpg%3Fitok%3DUBZfwNLI",
   },
 ];
 export default cookies;
 ```

8. Now we can access the `id` through `cookie.id` in the `.map()`.

 ```jsx
 const cookieList = cookiesData.map((cookie) => (
   <CookieItem cookie={cookie} key={cookie.id} />
 ));
 ```

Keep in mind that `key` can't be used, it's for the code not for us. If you take a look at the dev tools, you'll see that `key` is not in the `props` object, so we have no access to it.
