---
author: Alfresco Documentation
---

# Surf Framework Guide

Alfresco Surf lets you build user interfaces for web applications using server-side scripts and templates without Java coding, recompilation, or server restarts. Surf follows a content-driven approach, where scripts and templates are simple files on disk so that you can make changes to a live site in a text editor.

Surf is a Spring framework extension for building new Spring framework applications or plugging into existing Spring web MVC \(Model, View, Controller\) applications. Spring Web MVC provides separation between the application Model, View, and Controller \(known as *MVC*\). You can use Surf with other popular Spring Web MVC technologies including Tiles, Grails, and Web Flow.

Surf's object model lets you define pages, templates, components, and themes using XML. The Spring application picks up new files and processes them through scripts and templates to produce the view, and writes scripts using server-side JavaScript and Groovy. Templates are written using FreeMarker. You can build both page-centric and content-centric websites using Surf, and it provides out-of-the-box support for rendering content delivered through content delivery services, such as CMIS, Atom, and RSS.

**Note:** The Groovy invokedynamic `indy` library is included in Alfresco. Depending on the JVM version, you can target close to Java performance for dynamic Groovy with invokedynamic support activated.

## Features

-   **Scripts and templates**: Everything in Surf consists of scripts, templates, or configuration. This means no server restarts or compilation.
-   **Reusability**: Surf’s presentation objects, templates, and scripts emphasize reusability. Scoped regions and component bindings allow you to describe presentation with less code.
-   **Spring Web MVC**: Surf plugs in as a view resolver for Spring Web MVC, enabling you to use Surf for all or part of a site's view resolution. Surf renders views on top of annotated controllers and is plug-compatible with Spring Web Flow, Spring Security, Spring Roo, and Spring tag libraries.
-   **RESTful scripts and templates**: All page elements and remote interfaces are delivered through a RESTful API. The full feature set of web scripts is available to Surf applications. Write new remote interfaces or new portlets with a script, a template, and a configuration file.
-   **Content management**: A set of client libraries and out-of-the-box components streamline interoperability with CMIS content management systems, letting you easily access and present Enterprise content using Surf components and templates.
-   **Two-tier architecture**: Surf works in a decoupled architecture where the presentation tier is separate from the content services tier.
-   **Production, development, and staging/preview**: Configure Surf to work in a number of deployment scenarios including development, preview, or production environments.
-   **Development tools**: Tools that plug into the SpringSource suite of development tools include Eclipse add-ons for SpringSource Tool Suite, as well as Spring Roo plug-ins to enable scaffolding and script-driven site generation.

-   **[Surf content types](../concepts/surf-types-of-content(replace-surf-concepts).md)**  
In Spring Surf, content is devided into *Semantic content* and *Presentation content*, and the web application looks at both to render the final look of the Web page.
-   **[Content delivery services](../concepts/surf-content-delivery.md)**  
Surf connects to content delivery services to provide content retrieval and query for presentation and semantic content.
-   **[Content applications](../concepts/surf-content-apps.md)**  
Surf maintains a content-driven and scriptable approach to web application delivery, and interoperates well with Alfresco Web Content Management.
-   **[Model-View-Controller](../concepts/surf-mvc.md)**  
MVC applications use a dispatcher to handle requests for an application. It looks at the URL to determine which controller to invoke to set up a model, and then which view to invoke to render the model.
-   **[Spring Web MVC](../concepts/spring-web-mvc.md)**  
Spring Web MVC is the Model-View-Controller implementation for Spring framework web applications.
-   **[Surf View Composition framework](../concepts/surf-view-fwork-intro.md)**  
Surf provides a view composition framework.
-   **[Presentation content](../concepts/surf-pres-content.md)**  
Presentation content consists of templates, scripts, and XML files that Surf can pick up without a server restart.
-   **[Connectors and credentials](../concepts/surf-connectors-intro.md)**  
Web script developers often work with remote sources of data. Surf makes it easy to reach out to these information sources and pull together feeds of data.
-   **[Surf object XML quick reference \(siteData\)](../references/surf-object-xml-reference.md)**  
Surf objects are defined in XML. This document provides a quick reference guide to the most commonly used Surf objects, and how they are defined in XML.

**Parent topic:**[Share Architecture](../concepts/dev-extensions-share-architecture-extension-points.md)

