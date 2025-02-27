[//]: # (title: Get started with Kotlin/JS for React)

This tutorial demonstrates how to use IntelliJ IDEA for creating a frontend application with Kotlin/JS for React.

To get started, install the latest version of [IntelliJ IDEA](https://www.jetbrains.com/idea/download/index.html).

## Create an application 

Once you've installed IntelliJ IDEA, it's time to create your first frontend application based on Kotlin/JS with React.

1. In IntelliJ IDEA, select **File** | **New** | **Project**.
2. In the panel on the left, select **Kotlin Multiplatform**.
3. Enter a project name, select **React Application** as the project template, and click **Next**.
   
    ![Create a react application](js-new-project-1.png){width=700}
    
    By default, your project will use Gradle with Kotlin DSL as the build system.

4. Accept the default configuration on the next screen and click **Finish**. Your project will open.
  
    ![Configure a frontend application](js-new-project-2.png){width=700}

5. Open the `build.gradle.kts` file, the build script created by default based on your configuration. It includes
   the [`kotlin("js")` plugin and dependencies](js-project-setup.md) required for your frontend application. Ensure that
   you use the latest version of the plugin:

   ```kotlin
   plugins {
       kotlin("js") version "%kotlinVersion%"
   }
   ```

## Run the application

Start the application by clicking **Run** next to the run configuration at the top of the screen.

![Running a frontend app](js-run-app.png){width=500}

Your default web browser opens the URL [http://localhost:8080/](http://localhost:8080/) with your frontend application.

![Web browser with JS application](js-output-1.png){width=600}

Enter your name in the text box and accept the greetings from your application!

## Update the application

### Show your name backwards

1. Open the file `Welcome.kt` in `src/main/kotlin`.  
    The `src` directory contains Kotlin source files and resources. The file `Welcome.kt` includes sample code that renders 
    the web page you've just seen.
    
    ![Source code for frontend application](js-welcome-kt.png)

2. Change the code of `div` to show your name backwards.  
   
   * Use the standard library function `reversed()` to reverse your name.
   * Use a [string template](basic-types.md#string-templates) for your reversed 
   name by adding a dollar sign `$` and enclosing it in curly braces – `${name.reversed()}`.

   ```kotlin
   div {
        css {
            padding = 5.px
            backgroundColor = rgb(8, 97, 22)
            color = rgb(56, 246, 137)
        }
        +"Hello, $name"
        +" Your name backwards is ${name.reversed()}!"
    }
   ```

3. Save your changes to the file.

4. Go to the browser and enjoy the result.  
    You will see the changes only if your previous application is still running. If you've stopped your application, [run it again](#run-the-application).

![Web browser with a reversed name](js-output-2.png){width=600}

### Add an image

1. Open the file `Welcome.kt` in `src/main/kotlin`.  

2. Add a `div` container with a child image element `img` after the `input` block.  
   
   > Follow IDE suggestions to import all the required elements of the `react.dom.html` package.
   >
   {type="note"}
   
   ```kotlin
   div {
        img {
            src = "https://placekitten.com/408/287"
        }
    }
   ```

3. Save your changes to the file.

4. Go to the browser and enjoy the result.  
    You will only see the changes if your previous application is still running. If you've stopped your application, [run it again](#run-the-application).
   
![Web page with an image](js-output-3.png){width=600}

### Add a button that changes text

1. Open the file `Welcome.kt` in `src/main/kotlin`.  

2. Add a `button` element with an `onClick` event handler.  
   
   > Make sure that you import the relevant `react.dom.html.ReactHTML` element.
   >
   {type="note"}

   ```kotlin
   button {
        onClick = {
            name = "Some name"
        }
        +"Change name"
    }   
   ```

3. Save your changes to the file.

4. Go to the browser and enjoy the result.  
    You will only see the changes if your previous application is still running. If you've stopped your application, [run it again](#run-the-application).

![Web page with a button](js-output-4.png){width=600}

## What's next?

Once you have created your first application, you can complete long-form Kotlin/JS tutorials
or check out the list of Kotlin/JS sample projects for inspiration. Both types of resources contain useful snippets and
patterns and can serve as a nice jump-off point for your own projects.

### Tutorials

* [Build a web application with React and Kotlin/JS — tutorial](js-react.md)
guides you through the process of building a simple web application using the React framework, shows how a type-safe Kotlin
DSL for HTML makes it easy to build reactive DOM elements, and illustrates how to use third-party React components and
obtain information from APIs, all while writing the whole application logic in pure Kotlin/JS.

* [Building a Full Stack Web App with Kotlin Multiplatform](https://play.kotlinlang.org/hands-on/Full%20Stack%20Web%20App%20with%20Kotlin%20Multiplatform/01_Introduction)
teaches the concepts behind building an application that targets Kotlin/JVM and Kotlin/JS by building a client-server
application that makes use of shared code, serialization, and other multiplatform paradigms. It also provides a brief
introduction to working with Ktor both as a server- and client-side framework.

### Sample projects

* [Full-stack Spring collaborative to-do list](https://github.com/Kotlin/full-stack-spring-collaborative-todo-list-sample)
shows how to create a to-do list for collaborative work using `kotlin-multiplatform` with JS and JVM targets, Spring
for the backend, Kotlin/JS with React for the frontend, and RSocket.
* [Kotlin/JS and React Redux to-do list](https://github.com/Kotlin/react-redux-js-ir-todo-list-sample) implements
the React Redux to-do list using JS libraries (`react`, `react-dom`, `react-router`, `redux`, and `react-redux`)
from npm and Webpack to bundle, minify, and run the project.
* [Full-stack demo application](https://github.com/Kotlin/full-stack-web-jetbrains-night-sample) guides you through
the process of building an app with a feed containing user-generated posts and comments. All data is stubbed by
the fakeJSON and JSON Placeholder services.
