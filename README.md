# Docker sample with release workflow

## Docker Deployment Workflow
This uses [docker release workflow](https://github.com/kumvijaya/docker-release-workflow/blob/main/.github/workflows/ansible-cd.yml)

This is configured to run on-demand (on *workflow_dispatch*)

This workflow accepts below inputs
- **Release tag** : Required. The docker tag which to be used for deployment
- **Release version**: Required. The verison to deploy. Takes semantic version example *1.0.1*. 
Note: If the given release version not available, new release will be created and deployed.
- **Release description**: Optional. The description to use for creating new release in GitHub. This is used only when creating new release in GitHub.


This workflow has below steps:

- **Checkout**: Checksout the repository
- **Get Release**: Gets the release for the given release version inpt. This uses [git-get-release-action](https://github.com/cardinalby/git-get-release-action).
- Below steps executed only if the given release version not exists in the repository 
    - **Create Release**: This is executed only if the given release version not exists in the repository This uses [create release action](https://github.com/actions/create-release).
    - **Docker Build and Push**: This is executed only if the given release version not exists in the repository. Uses [Docker buildx action](https://github.com/docker/build-push-action)
- Use the given input version for deployment
    - Deployment steps to be added (**TODO**) 


<img width="940" alt="Screenshot 2023-02-19 at 11 04 27 PM" src="https://user-images.githubusercontent.com/121352639/220163337-062fa68c-0556-4e94-81a8-91e94273aab5.png">
