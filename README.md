# 01-fullstack-vendor-onboarding
# Trusted Vendors Portal – Full-Stack Assignment

## Objective
Welcome to your application assessment assignment. This is a chance for you to show us your coding and problem solving skills.
You are applying for a fullstack position so this assignment requires you to solve both frontend and backend challenges.

Nobody expects anyone to know everything so if a particular assignment is outside of your realm of experience, 
you may either skip it or propose a solution aligned with your experience.. 

In this repository, you'll find a basic demo implementation of the **Trusted Vendor Portal** application. 
Your task is to enhance and deploy this application by completing specific requirements listed below.

The system currently allows users to:
- Register a vendor (name, contact person, email, partner type [Supplier/Partner])
- View a list of registered vendors

---
## Vendor Object Example
    {
      "id": "1",
      "name": "Acme Freight",
      "contact_person": "John Doe",
      "email": "john.doe@acme.com",
      "partner_type": "Supplier" 
    }

## Existing Implementation

The repository contains:
- A Vue.js frontend application
- Two backend implementations (choose one):
  - Java (Spring Boot)
  - Node.js (TypeScript)

## Available Backends
You may choose which backend implementation to work with:

### Java (Spring Boot)
- Located in the `backend-java` directory
- Uses H2 in-memory database
- Includes basic create and list operations

### Node.js (TypeScript)
- Located in the `backend-node` directory 
- Uses SQLite database
- Includes basic create and list operations
---
## Your Tasks

### 1. Delete vendor
- Implement a delete functionality to allow users to remove vendor entries from the system
- Include a confirmation dialog before deletion to prevent accidental removal.
- Update both frontend and your chosen backend to support this feature

**solution**
1. Backend Changes
    1.1 Created new delete endpoint api/vendors/<id> on backend to take ID parameter and delete it from vendors table
2. Frontend changes
    2.1. Added Delete button on vendor list page which will call deleteItem function
    2.2 deleteItem function will show the confirmation dialog which when confimed will call the delete endpoint to delete the record.
   
### 2. Fix the UI bug
- Currently, clicking the "Add" button multiple times before the form resets can result in duplicate vendor entries.
- Prevent this behavior to improve the form UX

**solution**
1. Frontend Changes
    1.1 Updated the disable button logic to check for both loading and success flag
   
### 3. Unique Emails
- Ensure that vendor emails are unique across the system. If a user tries to register a vendor with a duplicate email, they should be informed of the conflict. 
  Think about where this logic should live and how the constraint is best enforced (frontend, backend, data storage or all) and justify your approach
- Document your reasoning

**solution**
1. Backend Changes
    1.1 Added Unique constraint on email column of vendors table.
    1.2 Updated the new vendor endpoint to check if email already exists. If it exists thow error message else insert the vendor details
2. Frontend changes
    2.1. Update the frontend logic to show proper error message
**reasoning**
    Email duplicate check is handled at both the backend and database layers.Unique constrint on the databse ensures no duplicate email address is inserted.backend duplicate check is done so that proper error message can be returned instead of relying on database error message.


### 4. Containerization & Deployment (Optional)
At maerks we host most of our backend services using pods and k8. If you have experience or find the challenge interesting, give this assignment a go.

Choose one of the following deployment approaches:

#### Option A: Docker Compose
- Containerize your chosen backend using Docker
- Create a Docker Compose configuration to run the entire system (frontend + backend)
- Include clear instructions to build and start the application

#### Option B (Advanced): Kubernetes/Minikube Deployment
- Create Kubernetes manifests (YAML files) for both frontend and your chosen backend
- Ensure services can discover and communicate (e.g., using `ClusterIP`)
- Use **Minikube** to test locally
- Provide clear documentation or scripts to:
  - Build and push Docker images to Minikube's Docker daemon
  - Apply Kubernetes configs to start the app

You're welcome to make UX improvements or add minor enhancements, as long as the core requirements are clearly addressed.

**My Views on Submission instruction questions:**
1. What do I love most about being a software engineer

   I am passionate about designing and building efficient, maintainable software solutions that solve real-world problems. I love leveraging my hands-on experience in both front-end and back-end development to build seamless, scalable web applications. I enjoy working with technologies like React, Node.js, and relational  databases to create user-friendly interfaces and reliable server-side logic. I am motivated by continuous learning and applying the best practices for developing the solutions
        
3. What is most important to me when it comes to working in a team
   
    The key thing I look for in a team is open communication, where everyone feels comfortable sharing their thoughts and progress. This helps build trust and ensures we’re all working toward the same goals.
I also appreciate a team environment that encourages collaboration and respects each person’s ideas, making it easier to solve any challenges together.
Its also important that everyone takes responsibility for their tasks so the team can run smoothly and deliver strong results.

4. What is the worst part of being a software engineer.
 
    The hardest part of being a software engineer is dealing with tight deadlines, which can sometimes be stressful and mean working longer hours. Fixing tricky bugs can also be frustrating because it takes time to find the problem. Also, technology changes fast, so you always need to keep learning new things, which can feel overwhelming sometimes. But I think these challenges help me get better and keep the job interesting.
---

## Evaluation Criteria
- **Code clarity & organisation** – Is the code readable, modular, testable and well-structured?
- **Testing** - How did you use testing to support your development efforts
- **Full-stack ownership** – Can you deliver a cohesive, working system with the required enhancements?
- **Pragmatism** – Did you make thoughtful decisions and sensible trade-offs?
- **DevOps awareness** – Is the system easy to build, run, and maintain?
- **Deployment quality** – If completed, is your containerization strategy practical, reproducible, and well-documented?"

---

## Submission Instructions

1. **Copy** this repository into your own GitHub account.
2. Complete the assigned tasks in copy.
3. **Documentation**
    1. Ensure your repository includes setup instructions and an updated README.md.
    2. Provide a short description of your approach to solving each task
    3. Highlight any assumptions, trade-offs, or challenges encountered during development.
4. In your readme.md file, also answer the following questions:
    1. What do I love most about being a software engineer.
    2. What is most important to me when it comes to working in a team
    3. What is the worst part of being a software engineer.
4. Share the link to your repository with us.
---

We're excited to see how you approach these tasks — feel free to get creative, make reasonable trade-offs, and show us how you think as an engineer. We're particularly interested in your understanding of full-stack development and DevOps practices.
