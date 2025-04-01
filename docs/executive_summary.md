---
lang: en
title: Project Requirements
viewport: width=device-width, initial-scale=1.0
---
# Project Requirements

## <a name="executive-summary"></a>Executive Summary

HERConnect HERBot is primarily an option-based chatbot which can be accessed on HERConnect's website. Although the chatbot is predominantly an option-based chatbot, user input is required when the user needs a followup. The chatbot functions as a wordpress plugin to allow for smooth integration of the chatbot on the HERConnect's wordpress website. Additionally, HERConnect Chatbot is an initiative born out of a collaboration between the City of Calgary, Calgary Police Services, Ladies in the Family Foundation (LIFF), Alberta Black Therapists Network (ABTN), and Health Research Partners (HRP) to address the gaps in mental health and provide information on social services for Black women and girls who have immigrated to Calgary within the past five years. The chatbot also serves as a culturally sensitive crisis response and follow-up system for the users. By leveraging the chatbot, users, including recent immigrants and the general Canadian public, can easily navigate crisis mental health services and newcomer resources, access multilingual support, and even book therapy appointments online, ultimately enhancing their mental well-being and fostering a sense of community support.

## <a name="project-glossary"></a>Project Glossary

- **Admin Dashboard** - Where the user will be able to make changes to prompts, resources, and languages.

- **Chatbot** - A computer program designed to simulate conversation with human users, typically over the internet.

- **Chat Service** - An application entity that includes the Chatbot.

- **Django HERBot Application** - Installed on a backend server, the application is responsible for providing an API for interacting with the business logic and storage of the application.

- **HERBot** - The total combination of our PHP plugin, Django HERBot applicatoin, and the Admin Dashboard.

- **Option-based chatbot** - A chatbot which asks the users to choose and click between the options provided to help the user reach their eventual goal purpose, resources in our case. Options help to guide the user to find their intended resource.

- **Category** - The different types of services (Mental Health, Immigration, Education, Recreation, Language Learning, Social Services, Employement, Clothing, Food, Religion and Housing) the chatbot can assist users with. For example, Mental Health is deemed a category. 

- **Options** - Buttons with text displayed by the chatbot which the user can click to identify their objective.

- **Natural Language Understanding (NLU)** - A field of computer science which analyzes what human language means, rather than simply what individual words say.

- **Crisis Response System** - A system designed to provide immediate assistance and support during emergencies or crises, such as mental health crises.

- **Culturally Sensitive** - Being aware of and responsive to the cultural norms, values, and beliefs of different groups, ensuring that interactions and services are respectful and inclusive.

- **Resource** - Piece of information that can include one or more of: name, website, email, contact, address and about, that helps the user accomplish a task, achieve a goal, or address a need.

- **Emergency** - A situation when the user is in need of immediate professional help.

- **Coordinated Access to Care** - A system or process that ensures seamless and efficient access to healthcare services, often involving collaboration between different healthcare providers and organizations.

- **Unified System** - A system that integrates multiple components or functions into a single, cohesive platform, providing a unified user experience.

- **Multilingual Support** - The ability of a system or platform to operate and provide content in multiple languages, accommodating users who speak different languages.

- **Personalized Recommendations** - Suggestions or advice tailored to the individual preferences, needs, or characteristics of users, based on data analysis or user input.

- **Plugin** - A piece of software that adds specific features or functionality to an existing computer program or system, typically extending its capabilities.

- **MySQL** - A popular open-source relational database management system used for storing and managing data.

- **PHP** - A server-side scripting language commonly used for web development, often used in conjunction with databases like MySQL.

- **WordPress** - A widely-used open-source content management system for creating and managing websites, known for its flexibility and ease of use.

- **WordPress Application** - Wordpress is a PHP application. It's primary code is written in PHP and it works with a mySQL database as the backend.

- **WordPress Site** - A website that has Wordpress installed.

- **Apache License** - A permissive open-source software license that allows users to use, modify, and distribute software freely, with some conditions.

- **User-Response Time** - The time it takes for a system to respond to user inputs or requests, often measured in milliseconds or seconds.

- **Usability** - The degree to which a system is user-friendly and easy to use, typically assessed based on factors such as learnability, efficiency, and satisfaction.

- **Security** - Measures and protocols implemented to protect a system or application from unauthorized access, data breaches, and other security threats.

- **Semgrep** - A static analysis tool.

(Part of the above glossary was generated from ChatGPT 3.5 with an input of project information, and the prompt "Give me a project glossary. Project glossary include meanings of words commonly used within chatbot developing which the general people might not be aware of", 2024-01-25)

## <a name="user-stories"></a>User Stories
## Chatbot Initiation
### US 1.01 - Chatbot Access
> **As** a User, **I want** to be able to have access to chatbot on the HERConnect website.

> **Acceptance Tests**

> 1. The chatbot should be visible on the HERConnect website.
> 2. The chatbot should be functional on the HerConnect website.

### US 1.02 - Multilingual Text Conversation
> **As** a User, **I want** to be able to ask the chatbot questions in English, French or Swahili, **so that** I can use a language I am comfortable with.

> **Acceptance Tests**

> 1. The chatbot allows the user to type text in English, French or Swahili language.
> 2. The chatbot interprets the user’s request correctly within the chosen language’s context.

### US 1.03 - Multilingual Audio Output
> **As** a User, **I want**  I want the chatbot to be able to speak its reply to me, **so that** it is easier to communicate with.

> **Acceptance Tests**

> 1. The chatbot outputs in an audio format in the language chosen by the user.
> 2. The chatbot’s audio output should make total sense to a native speaker in the user’s chosen language.

## Chatbot Function

### US 2.01 - Newcomer Resources

> **Note:** This User story encompasses all the different categories of newcomer resources excluding the housing resource. 

> **As** a User, **I want** to be able to find newcomer resources through the chatbot conversation, **so that** I get help with newcomer services.

> **Acceptance Tests**

> 1. When asking to find newcomer resources, the chatbot provides the relevant information. Relevant information includes at most the top 3 resources that align with the recent/last subcategory the user chooses. The different categories of resources include:
    - Immigration Resources
    - Education Resources
    - Recreation Resources
    - Language Learning Resources
    - Social Service Resources
    - Employment Resources
    - Mental Health Resources
    - Clothing Resources
    - Food Resources
    - Religion Resources

> 2. Links, addresses and contact information are provided as necessary.
     - If the list of resources are more than three, provide a link to the HERConnect's resources webpage after listing the three resources
> 3. Within mental health services, the chatbot should provide the user with therapist booking services if deemed fit.


### US 2.02 - Housing Resources
> **Note:** Housing resource is deemed a seperate user story because this was part of sprint 2 and includes the whole code constructing a chatbot conversation flow. Once, we have this conversational flow coded, the rest of the resource categories follow this code with just the contnt changing.

> **As** a User, **I want** to be able to find housing resources through the chatbot conversation, **so that** I get help with housing services.

> **Acceptance Tests**

> 1. When asking to find housing resources, the chatbot provides the relevant information. Relevant information includes at most the top 3 resources that align with the recent/last subcategory the user chooses
> 2. Links, addresses and contact information are provided as necessary.
     - If the list of resources are more than three, provide a link to the HERConnect's resources webpage after listing the three resources

### US 2.03 - Start Over
> **As** a User, **I want** I would like to be able to start over chatbot, **so that** I can start a fresh chat.

> **Acceptance Tests**

> 1. When clicking on the ‘start over’ button, chatbot will guide the user back to language selection and start a new conversation session.

## Chatbot Ending/Termination
### US 3.01 - Negative feedback
> **As** an Administrator, **I want** to see if any of the chat users are not satisfied with the results of the chat, **so that** I can improve/update the chatbot when needed.

> **Acceptance Tests**

> 1. Chatbot should ask for a star rating near the end of the conversation, i.e., after providing the resources.
> 2. If the user indicates less than 4 stars (1, 2 or 3 stars), the chatbot will provide a link to provide feedback (HERCOnnect feedback form).

### US 3.02 - Positive feedback
> **As** an Administrator, **I want** users who enjoy their chat experience to leave a review on Google Business, **so that**  our business can build a good reputation.

> **Acceptance Tests**

> 1. Chatbot should ask for a star rating near the end of the conversation, i.e., after providing the resources.
> 2. If the user indicates 4 or 5 stars in the rating, the chatbot will respond by providing a link to HERConnect’s Google business review page.

### US 3.03 - Customer Service Redirect
> **As** a User, **I want** to talk to a human representative if I do not feel the chatbot’s response is sufficient, **so that** I get full customer service on finding resources.

> **Acceptance Tests**

> 1. Chatbot should give the contact information of the link agent (customer service agent) near the end of the conversation, i.e., after providing the resources.

### US 3.04 - User Followup
> **As** a User, **I want** the chatbot to ask for and setup a follow up with a HERConnect's customer service agent, **so that** I get adequate help.

> **Acceptance Tests**

> 1. Near the endpoint (i.e., displayed resources), Chatbot should ask the user if they need a follow up.
> 2. If user needs follow up, ask for user's name, phone number and email.
> 3. Auto send the user's chatbot session and contact information (name, phone number and email) to the link worker's email.
    - Do not save the user's personal information in database.

## Other Requirements
### US 4.01.01 - Admin Login
> **As** an Administrator, **I want** only authorized users (i.e., somebody from HERConnect team) to access the chatbot admin dashboard, **so that** only my team can make changes to messages, resources and languages. 

> **Acceptance Tests**

> 1. When the correct username and password is provided, the user is forwarded to the dashboard.
> 2. When the incorrect username and password is provided, the user is not forwarded to the dashboard.

### US 4.01.02 - Update Messages

> **As** an Administrator, **I want** to add, delete and update messages and options, **so that** I can control the content of the chatbot. 

> **Acceptance Tests**

> 1. When admin adds a new option, a new option and its associated new next message (empty at the time) is created in the database.
> 2. When admin makes changes to existing messages and options, the associated messages and options should be updated in the database.
> 3. When admin deletes any message or option, the cascading messages or options should be deleted in the database.

### US 4.01.03 - Update Resources
> **As** an Administrator, **I want** to add, delete and update resources, **so that** I can control the resources outputed by the chatbot. 

> **Acceptance Tests**

> 1. When admin adds a new resource, a new resource is created in the database.
> 2. When admin makes changes to existing resources, the associated resources should be updated in the database.
> 3. When admin deletes any resource, the associated resources should be deleted in the database.

### US 4.01.04 - Update Language
> **As** an Administrator, **I want** to add, delete and update languages, **so that** I can specify what languages the application will use.

> **Acceptance Tests**

> 1. The admin can add a new language.
> 2. The admin can remove a language. 
> 3. The admin can update the language name. 
> 3. When a new language is added, the admin can now add a message, option and resource information for that language. 


### US 4.02 - Loading Time

> **As** a User, **I want** to start using the chatbot without waiting too long, **so that** I don't waste time.

> **Acceptance Tests**

> 1. Initial load of chatbot should be less than 10 seconds.
> 2. Responses are returned in less than 5 seconds.



## <a name="moscow"></a>MoSCoW
### Must Have
* US 1.01 - Chatbot access
* US 2.02 - Housing resources
* US 2.01 - Newcomer Resources
* US 1.02 - Multilingual Text Conversation
* US 4.01.01 - Admin Login
* US 4.01.03 - Update Resources
* US 4.01.02 - Update Messages

### Should Have
* US 3.03 - Customer Service Redirect
* US 2.03 - Start Over
* US 3.04 - User Followup

### Could Have
* US 3.02 - Positive Feedback
* US 3.01 - Negative Feedback
* US 4.01.04 - Update Language

### Would Like But Won't Get
* US 1.03 - Multilingual Audio Output
* US 4.02 - Loading Time

## <a name="similar-products"></a>Similar Products
* [UofA Live Chat](https://www.ualberta.ca/information-services-and-technology/chat.html)
    - University's Vera chatbot
    - Vera acts as the live online assistant to Ualberta students as it has access to all the Ualberta's website information and can respond with relevant information from the user inquiries
    - Take inspiration: chatbot's placement in a website page, chatbot's UI, chatbot's essential features (security, transparency and useability)
* [WPBot](https://wordpress.org/plugins/chatbot/#description)
    - AI ChatBot
    - WordPress Plugin
    - Initial is free
    - Can work as Button Menu Driven, NLU or combination of both
    - Understand the WordPress Plugin process and take inspiration from how the code is structured/architectured

## <a name="open-source-projects"></a>Open-source Projects
* [Rasa](https://github.com/RasaHQ/rasa)
    - Chatbot framework
    - Programming languages/frameworks: Python
    - Take inspiration from how the chatbot features such as Gui or admin are set up
* [Botpress](https://github.com/botpress/botpress)
    - Chatbot framework
    - Programming languages/frameworks: Typescript and Node.js
    - Take inspiration from how the chatbot features such as Gui or admin are set up
* [Microsoft Bot](https://github.com/microsoft/botframework-sdk)
    - Chatbot framework
    - Programming languages/frameworks: Various (Python, Java, C# or Javascript)
    - Take inspiration from how the chatbot features such as Gui or admin are set up

## <a name="technical-resources"></a>Techincal Resources
### Backend: SQLite + Django
  * [SQLite](https://www.sqlite.org/)
  * [Django](https://www.djangoproject.com/)

### Deployment: Docker + Cybera
  * [Docker](https://www.docker.com/)
  * [Cybera](https://www.cybera.ca/rapid-access-cloud//)
  * [Deploy using Cybera + Docker + Django](https://docs.google.com/presentation/d/1Lqq1r1xQFIjbf_VffKeUopTCK1l77R0gHLkclCI1s8w/edit)
  
### Frontend: Javascript + Vanilla.js + PHP + React
  * [Javascript](https://www.javascript.com/)
  * [PHP](https://www.php.net/)
  * [Vanilla.js](http://vanilla-js.com/)
  * [React](https://react.dev/)
#### ReactFlow
  * [React Flow Dagre Layout with Custom Nodes](https://ncoughlin.com/posts/react-flow-dagre-custom-nodes/)
  * [React Flow](https://reactflow.dev/)
#### Analysis
  * [semgrep](https://semgrep.dev/)