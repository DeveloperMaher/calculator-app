# Angular Calculator CI/CD Pipeline on AWS

A fully automated CI/CD pipeline for a Sample Angular Calculator Application. This project demonstrates how to integrate **GitHub**, **AWS CodePipeline**, **AWS CodeBuild**, and **Amazon S3** to achieve continuous integration and continuous deployment (CI/CD).

![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

## 📖 Project Overview

This repository contains a sample Angular Calculator application created for the **Solutions Architect Path**. The primary focus of this project is the infrastructure and deployment strategy, showcasing a seamless CI/CD workflow. 

Whenever code is pushed to the `main` branch of this GitHub repository, AWS CodePipeline automatically triggers a build via AWS CodeBuild and deploys the static files to an Amazon S3 bucket configured for static website hosting.

### 🔗 Live Demo
You can view the deployed application here: [http://calculator.omlo-dev.click](http://calculator.omlo-dev.click) *(Note: HTTP might be used depending on the S3 setup)*

---

## 🏗️ Architecture & CI/CD Flow

The following diagram illustrates the automated deployment pipeline:

```mermaid
graph LR
    Dev[Developer] -->|Push Code| GH[GitHub Repository]
    
    subgraph AWS Cloud
        CP[AWS CodePipeline]
        GH -->|Stage 1: Source| CP
        
        CB[AWS CodeBuild]
        CP -->|Stage 2: Build| CB
        
        S3[Amazon S3 Bucket]
        CP -->|Stage 3: Deploy| S3
    end
    
    S3 -->|Static Website Hosting| User[End User / Browser]
