# How to Create a Private Registry in Docker Hub

## 1. Create a Docker Hub Account
   - Go to [Docker Hub](https://hub.docker.com/).
   - Click on **Sign Up** and create an account by providing your email, username, and password.

## 2. Log into Docker Hub
   - Once you have an account, log in to Docker Hub at [Docker Hub Login](https://hub.docker.com/).

## 3. Create a New Repository
   - After logging in, click on your profile icon at the top-right corner and select **Repositories**.
   - Click on **Create Repository**.
   - Fill in the repository details:
     - **Name**: Choose a name for your repository.
     - **Description**: (Optional) Describe what this repository is for.
     - **Visibility**: Set this to **Private**.
   - Click on **Create**.

## 4. Push Images to Your Private Repository
   - Now, you need to push Docker images to your private registry. First, log in to Docker Hub via the command line by running:

     ```bash
     docker login
     ```

     Enter your Docker Hub credentials (username and password).

   - Tag your image with the repository name in Docker Hub. For example:

     ```bash
     docker tag my-image:latest your-dockerhub-username/my-repository:tag
     ```

   - Then push the image to your private registry:

     ```bash
     docker push your-dockerhub-username/my-repository:tag
     ```

   This will upload the image to your private Docker Hub repository.

## 5. Accessing the Private Registry
   - Your images are now stored in a private repository on Docker Hub. To pull an image from this private repository, you will need to authenticate using the same credentials:

     ```bash
     docker login
     docker pull your-dockerhub-username/my-repository:tag
     ```

## 6. Managing Your Private Repository
   - You can manage your private repositories via the Docker Hub website, where you can:
     - **Change visibility** (from private to public).
     - **Delete** repositories.
     - **Set permissions** (e.g., allowing other Docker Hub users to access the repository).

## Important Notes:
- Private repositories on Docker Hub are free for individual users, but there are limits to the number of private repositories you can have. You can check Docker Hub's [pricing page](https://www.docker.com/pricing/) for more details on private repository limits.
  
- You can control access by inviting collaborators to your private repository from the Docker Hub interface.

With these steps, you've created a private registry on Docker Hub and can securely store and access your Docker images.


## Setting Up RBAC (Role-Based Access Control) for Docker Hub

Role-Based Access Control (RBAC) helps you manage permissions for users interacting with your Docker Hub repository.

### 1. Create Teams for Your Organization

- To enable RBAC, you must first create an organization and then create teams within that organization.
- Go to [Docker Hub](https://hub.docker.com/) and select "Organizations" from the dropdown under your profile.
- Click on "Create Organization" and follow the prompts to set up an organization.
- Once your organization is created, create teams within it by selecting "Teams" from the organization's page.

### 2. Assign Roles to Teams

- Inside your organization, you can assign roles to each team.
- Roles include:
  - **Owner**: Full administrative rights to the organization.
  - **Manager**: Can manage repositories, but cannot transfer the organization.
  - **Developer**: Can push and pull images from repositories.
  - **Guest**: Can only pull images from repositories.
  
- Navigate to the team settings and assign roles to users within that team.

### 3. Assign Repository Access

Once you have teams set up, go to the "Repositories" section in your Docker Hub organization. Select the repository you want to manage permissions for and assign specific roles to teams (e.g., "Developer," "Manager").
