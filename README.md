# CST8915 Lab 2 - 12-Factor App Microservices Deployment

**Student:** Jesse Kinsella
**Course:** CST8915 - Full-stack Cloud-native Development  
**Lab:** Lab 2

---

## Demo Video

[Watch the Lab 2 Demo Video](https://youtu.be/XFTNlCiePh0)

---

## Service Repositories

- [Order Service](https://github.com/LostAlpaca1/CST8915-Lab2-Order-Service)
- [Product Service](https://github.com/LostAlpaca1/CST8915-Lab2-Product-Service)
- [Store Front](https://github.com/LostAlpaca1/CST8915-Lab2-Store-Front)

---

## Reflection Questions

### 1. What changes did you make to the order-service and product-service to comply with the Configurations and Backing Services factors of the 12-Factor App methodology?

For the order-service, I moved things like the port and RabbitMQ connection information into environment variables instead of keeping them directly in the code. I did something similar with the product-service by having its port come from an environment variable. I also had the order-service connect to RabbitMQ as a separate backing service running on its own VM. I used `.gitignore` so that my local `.env` files, especially the one containing the RabbitMQ login information, would not be uploaded to GitHub.

### 2. Why is it important to use environment variables instead of hard-coding configurations in your application?

Using environment variables makes it much easier to change where or how an application is running without having to edit the actual code every time. This was useful in this lab because each service was running on a different Azure VM, so things like IP addresses and connection information could be changed through the environment. It is also much safer for information like passwords because I can keep my `.env` file out of GitHub instead of accidentally putting credentials into my repository.

### 3. Why is it important to have separate repositories for each microservice? How does this help maintain independence and scalability of each service?

Having a separate repository for each microservice keeps the services independent from each other. In this lab I had separate repositories for the order-service, product-service, and store-front, so I could work on one without having to change the others. I think this would become even more useful with a larger application because each service could be updated, deployed, or scaled on its own depending on what that specific service needs.
