# System's Configuration Management

This project is an umbrella and the git repository is used only for documentation.
The sub-projects of System's Configuration Management live in a different Github repositories (see [projects](#projects)).

## Table Of Content
* [What is SCM?](#what-is-scm)
* [Projects](#projects)
* [Structure](#structure)

## What is SCM?

*System's Configuration Management (SCM)* is a system that provides centralized aggregation, storage and distribution of configuration changes in the system.

Let's imagine that you have a system that contains a large number of instances and you what track all configuration changes in it: check changes for specified time period, compare changes with  template after update or build graph of connection between instances. SCM provide ready for use infrastructure that help resolve all above tasks. You need only integrate to the service instance mechanism for sending messages and configure it. All other operation takes over system components.

SCM contains *persistent storage* for events, so history will be saved and can be obtained at any time.

Management system provides components for messaging and subscribing to event broadcast. It allows extend system with new applications to construst other projection of system configuration or any else that use configuration changes information.

## Projects

Project contains four projects that provides main components of the system:

* [scm-messaging](https://github.com/ametiste-oss/ametiste-scm-messaging) - messaging components;
* [scm-coordination](https://github.com/ametiste-oss/ametiste-scm-coordination) - coordination components;
* [scm-message-broker](https://github.com/ametiste-oss/ametiste-scm-message-broker) - message broker application;
* [scm-event-log](https://github.com/ametiste-oss/ametiste-scm-event-log) - event log application.

More detailed information about any of project you can read in corresponding repository.

## Structure

Main core components are **Event Sender** and **Event Receiver**. This components responsible to transport eventd between system components. Configuration changes represents as **Event** incapsulated in **Message** with specified structure. This three components contains in Message Protocol Library.
Any application that want's transport messages must use this components. It unifies transmission mechanism and simplifies changes when necessary.

Coordination components provide mechanism to fetch subscribers and subscribe to event broadcast. Any application may include subscriber component and Event Receiver and receive event messages.

Below show structure diagram with main components:

![SCM infrastructure scheme](https://cloud.githubusercontent.com/assets/11256858/10566739/22decf70-75f8-11e5-9234-df14c08c929e.png)

System also contains two service: **Message Broker** and **Event Log**. **Broker** organize event broadcast, **Log** save events to persistent storage.

It's minimal structure of system that may be simply extend.
