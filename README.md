# symfony-react
Combining React and Symfony
Contemporarily, modern web applications built with PHP framework like Symfony now require implementation of a huge amount of logic on the frontend in order to create a rich web experience for users. This is mostly handled by jQuery back in the days, but at the moment, there are numerous awesome frontend libraries available in the market. They include, but are not limited to Angular, Ember, Vue and React. With these several options, one can easily get lost and spend quite a bit of time deciding on which of the library is more compatible with Symfony.

To make things easier, Symfony unlike its major contender in the PHP world (Laravel), does not favor a particular library or frontend framework over another. It remains absolutely neutral to your choice of the library that runs on the client side of your application. This leaves you with an opportunity to explore the world of JavaScript and work with any of the modern frontend library for building single page applications that you are quite comfortable with.

However, as at the time of writing, React is the most prominent library for building reusable user interface components. As you proceed with this post, you will realise how easy it is to combine React and Symfony together in a single project successfully. Thanks to the introduction of a pure-JavaScript library called Symfony Webpack Encore, it is now simple to manage JavaScript files in a Symfony-based application, as it offers a simplified process for working with both CSS and JavaScript.

What You Will Build with React and Symfony
As pointed out at the beginning of this post, you will learn how to build a secured application with React at the frontend and a Symfony powered backend API. This application will allow users to fetch protected information from the API only if they are authenticated and give full access to a public route for all users ( authenticated and non-authenticated) as depicted by the images below:

Developing Modern Apps with Symfony and React

Showing scured route developed with Symfony and React

Traditionally, Symfony usually handles everything from the state management, page rendering and routing when developing web applications with it. Here, you will deviate a little from totally building Symfony applications that way, as you will learn a different approach to page rendering, routing and state management.

Structure of the application
The frontend of the application will be broken into different reusable and independent UI components. Here, you will use React to render contents without necessarily requesting a new page from the server or refreshing the page before navigating to a new route. This is one of the beauties of single-page applications.

Once a user tries to fetch information from a protected route, that will be defined later in this post, they will be redirected to Auth0 to get authorized and afterwards, they will be redirected back to the app.

For the backend, you will simply use Symfony to accept and process HTTP requests sent in by React and return the appropriate information based on the authentication status of the user.

With the structure and basic information about the application that will be built in this post properly covered, you can now proceed to start building the application.

Scaffolding the Symfony Application
Here, to start building the backend API, you will install and set up a Symfony application via Composer. To do this, you need to access the terminal in your operating system, navigate to your development directory and run the following command to install a project named symfony-auth0-api on your machine:

composer create-project symfony/website-skeleton symfony-auth0-api
Once the installation process of Symfony and the respective required bundle by Composer is completed, change directory into the newly created folder with:

cd symfony-auth0-api
Creating the Symfony Backend API
Leverage the Symfony maker bundle to create a controller for the API with:

php bin/console make:controller SecuredController
The preceding command will create a new file named SecuredController.php which can be found in src/Controller folder and a template file in templates/secured/index.html.twig. You can ignore the template file for now, but open the newly created SecuredController.php and add the following content:
