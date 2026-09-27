# Lecture 1: Internet of Things

> **IoT | Inter(net) of Thing(s)**  
> Source: [IoT course lecture 01](https://kurzy.kpi.fei.tuke.sk/iot1/lectures/01/)

## 1. What is IoT?

The **Internet of Things (IoT)** is a paradigm in which ordinary objects and devices become connected participants in a network. They can sense their environment, exchange data, be monitored, and sometimes control other devices.

The important distinction is:

> A smart device is not automatically an IoT solution.

IoT becomes meaningful when connected things cooperate, exchange information, and provide **added value** such as automation, monitoring, optimisation, or better decisions.

## 2. From a thing to IoT

| Stage | Description | Example |
| --- | --- | --- |
| **1. Thing** | A device works locally but does not provide extra functionality through a network. | A light bulb switched on by a wall switch. |
| **2. Smart device** | The device can communicate with a user or another device. It can report its state or receive commands. | A lamp controlled and dimmed from a mobile app. |
| **3. Network of smart devices** | Several smart devices cooperate through a local network or a management platform. | A weather station, gate sensor, and lamp trigger an automation. |
| **4. Internet of Things** | Connected devices become part of a wider network and can exchange data beyond one local installation. | Energy meters, homes, batteries, and electric cars coordinate their behaviour. |

The Internet is therefore not the only important part. The devices, communication, data processing, users, and resulting service all matter.

## 3. Four-layer IoT architecture

### Layer 1: Things, sensors, and actuators

This layer contains the physical devices that observe the environment or act on it.

- **Sensors** measure values such as movement, light, temperature, fill level, or energy consumption.
- **Actuators** perform actions, for example switching a light, opening a valve, or sounding an alarm.
- Devices may communicate with a gateway, but local device-to-device communication is also possible.

Local communication is useful when an action must be fast. For example, a movement sensor can trigger a light without sending the event to a distant cloud first.

### Layer 2: IoT gateways and data collection

A gateway is located close to the devices. It collects, aggregates, filters, and converts raw data before forwarding it to higher layers.

Typical gateways include a smart-home hub, an industrial gateway, a Wi-Fi router with IoT functions, or a USB coordinator. Gateways are useful because they:

- reduce the amount of data sent to the cloud;
- translate between device protocols;
- provide initial processing and visualisation;
- improve security by controlling traffic between layers.

### Layer 3: Edge analytics

**Edge computing** moves computation and storage closer to the devices that produce or need the data. This reduces response time and bandwidth usage.

Edge systems can analyse data, provide fast local responses, and synchronise selected results with central systems. They are especially useful in industry or other situations where latency matters. An edge layer is helpful, but not required in every IoT solution.

### Layer 4: Data centres and cloud platforms

Cloud or local data-centre systems provide large-scale storage, processing, analytics, machine learning, dashboards, and user applications.

This layer can handle much more data and computing than most edge devices. It supports long-term analysis and business decisions, but it may be geographically far from the physical devices.

## 4. Example: smart waste collection

Consider waste containers equipped with sensors:

1. A sensor measures the container's fill level.
2. A gateway collects readings from many containers and filters unnecessary messages.
3. Edge infrastructure analyses local data and prepares routes or alerts.
4. A cloud platform stores historical data, creates dashboards, and optimises collection schedules.

The basic service is still waste collection. IoT adds value through better routes, fewer unnecessary trips, lower operating costs, and potentially a fairer price based on actual service usage.

## 5. Important design questions

An IoT solution should consider more than electronics:

- What data is collected and why?
- Which device or layer should process it?
- How do devices communicate and authenticate?
- What happens when the connection is unavailable?
- How are devices updated and protected?
- What useful decision or automation does the data enable?

Not every solution needs all four layers. A small local system may use only devices and a gateway, while a large service may use all layers.

## Exam checklist

- Explain why a smart device alone is not an IoT solution.
- Describe the progression from a thing to the Internet of Things.
- Name and explain the four IoT architecture layers.
- Distinguish sensors, actuators, gateways, edge systems, and cloud platforms.
- Explain why gateways filter and aggregate data.
- Explain the purpose of edge computing.
- Identify the added value in the smart waste-collection example.

### Key takeaway

IoT is a connected system of things, communication, data processing, and services. Its purpose is not merely to connect hardware, but to turn data and cooperation between devices into useful added value.