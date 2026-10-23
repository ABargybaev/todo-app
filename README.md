# Lab 3: CI/CD with GitHub Actions

## Goal

Learn how to use GitHub Actions to test code, build Docker images, and publish them to Docker Hub automatically.

## Tools

- Git
- GitHub
- GitHub Actions
- Python
- Flask
- Pytest
- Docker
- Docker Hub

## What I Did

1. Created a Flask ToDo application.
2. Ran 4 tests locally using pytest.
3. Created a public GitHub repository.
4. Created a CI workflow in `.github/workflows/ci.yml`.
5. Tested automatic workflow execution.
6. Changed the code to make one test fail.
7. Fixed the error and ran the tests again.
8. Created a Docker Hub access token.
9. Added the token and username to GitHub Secrets.
10. Added a Docker build and push job.
11. Published the Docker image to Docker Hub.
12. Downloaded and tested the Docker image.
13. Created a new Git branch and added a fifth test.
14. Created a Pull Request and checked the workflow.
15. Merged the Pull Request into main.

## How CI/CD Works

When I push code to the main branch, GitHub Actions automatically:

1. Downloads the code.
2. Sets up Python.
3. Installs dependencies.
4. Runs pytest tests.
5. Builds a Docker image if the tests pass.
6. Publishes the image to Docker Hub.

## Testing

At first, all 4 tests passed.

Then I changed the health response from `ok` to `OK`.

The `test_health` test failed because it expected `ok`.

I fixed the code and pushed it again. All tests passed.

Later, I added a fifth test in a new branch.

## Docker Hub

Docker image:

https://hub.docker.com/r/abargybaev/todo-app

The image has two tags:

- `latest`
- Commit SHA

## Docker Test

I downloaded the Docker image and started a container.

I checked:

- `GET /health`
- `GET /todos`
- `POST /todos`

Everything worked successfully.

## Pull Request

I created a branch called `feature/new-test`.

I added a new test and opened a Pull Request.

GitHub Actions ran the tests, but the `build-and-push` job was skipped.

After merging into main, both jobs ran successfully.

## Questions and Answers

**1. Which test failed and why?**

The `test_health` test failed.

The application returned `OK`, but the test expected `ok`.

After fixing the code, all tests passed.

**2. Why was build-and-push skipped in the Pull Request?**

Because the workflow only publishes Docker images from the main branch, not from Pull Requests.

**3. Why do we need a commit SHA tag if we already have latest?**

The `latest` tag points to the newest image.

The SHA tag identifies the image built from a specific commit.

It helps us find and use an older version if something goes wrong.

## Result

The lab was completed successfully.

I learned how to create CI/CD pipelines, run automatic tests, use GitHub Secrets, publish Docker images, and work with Pull Requests.