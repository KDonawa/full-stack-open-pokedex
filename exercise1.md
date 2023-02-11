## CI/CD pipeline in python

For python we can use git for version control, Github for hosting and CircleCI as the external continuous integration service.

Let's say we are building a simple calculator app with four basic methods for

- addition,
- subtraction,
- multiplication
- division

We start by implementing the addition and subtraction methods.

Next we handle testing which is done in two steps:

1. First a linter to analyze the code for potential errors and ensure it is easier to read (flake8 can be used to do this)
2. Then you write unit tests to check if both functions work as expected (pytest can be used for unit testing).

The standard practice in unit testing is to look at code coverage which represents the percentage of the code that is covered by your tests.

Once all the tests have passed and we are confident that our code works we commit the changes (methods and their tests) to the main branch

### Set up the CI/CD pipeline.

CircleCI requires a .circleci folder within your repo and a configuration file (config.yml) inside it. The steps for the pipeline are added to this config file. CircleCI also maintains pre-built Docker images for several programming languages including Python. That image will create a container (virtual environment) in which everything else happens.

The pipeline consists of 3 steps:

1. checking out the repository
2. installing the dependencies in a virtual environment
3. running the linter and tests while inside the virtual environment.

You can then start the build process from the CircleCI dashboard. Now, every time code is pushed to the main branch, a job will the triggered.

### Add code changes

Add the multiplication method, write the tests and push to the main branch. The pipeline will execute and the job will be successful if the tests pass.

Then repeat for the division method and so on.

### Self-hosted vs Cloud-based

For the case of 6 people working on an app, choosing between a self-hosted or a cloud-based environment will largely depend on the build times for the pipeline which will depend on its size. An app with a team of 6 should not be too large so the cloud environment will likely be the preferred option.
