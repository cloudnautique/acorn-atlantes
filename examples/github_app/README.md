# How to use this example

This deploys an Atlantis server setup with GitHub app auth. It also illustrates how to pass configuration to the server via the primary interfaces.

## Prerequisites

Make sure you are all set to run Acorn.

- [Acorn CLI](https://docs.acorn.io/install)

## Deploy

This requires two steps to bootstrap for the first time.

1. Clone this repo.
1. Cd into the `examples/github_app` directory.
1. Edit the Acornfile to set the `--repoAllowList`. (Must be non-empty string)
1. Create an envconfig secret. (This can be changed later)

    ```shell
    acorn secret create envconfig --data TF_VAR_placeholder=foo
    ```

1. Start the App

    ```shell
    acorn run -n atlantis .
    ```

1. Open Acorn platform UI. `acorn dashboard` from a separate terminal.
1. Expand the `atlantis` instance.
1. Click the link to the first "Secret Create Helper".

    a. Fill in the form. This will set the basic auth credentials for the Atlantis web app.

    b. Click submit and close the tab/window.

1. Click the link to the second "Secret Create Helper" in the Acorn UI.
1. Go back to the Acorn dashboard and click the link to launch the Atlantis UI.

    a. Log in with username and password (atlantis/atlantis)

    b. Append `/github-app/setup` to the URL and hit enter.

    c. Click the Setup button.

    d. Follow instructions on the GitHub side.

    c. When back to the Atlantis UI, click the install App link at the top of the page. Follow those instructions.

1. Copy the App ID, Key, and Webhook secret into the "Secret Create Helper" form.
1. Click submit and close the tab/window.
1. The terminal that originally started the app should now be completed. Update the app to enable the new settings:

    ```shell
    acorn run -n atlantis --update . --bootstrap=false
    ```

1. Now you can start using Atlantis. The credentials to the Atlantis UI are now what was set in step 8 and will no longer be `atlantis:atlantis`.
