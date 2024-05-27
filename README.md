# dockansible
Using multi-stage Docker builds helps in creating lean and optimized Docker images. By separating the build and runtime stages, we can ensure that only the necessary files are included in the final image, reducing the image size and improving security. The build stage includes all the dependencies and tools needed to compile the application, while the runtime stage only contains the application files and the necessary runtime environment, resulting in a smaller and more efficient Docker image.

# Execute the playbook to install Node.js.
ansible-playbook ansible/install_nodejs.yml
