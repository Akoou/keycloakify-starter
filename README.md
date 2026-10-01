<p align="center">
    <i>🚀 <a href="https://keycloakify.dev">Keycloakify</a> v11 starter 🚀</i>
    <br/>
    <br/>
</p>

# Quick start

```bash
git clone https://github.com/keycloakify/keycloakify-starter
cd keycloakify-starter
yarn install # Or use an other package manager, just be sure to delete the yarn.lock if you use another package manager.
```

# Testing the theme locally

[Documentation](https://docs.keycloakify.dev/testing-your-theme)

# Enable passkey sign-in

This theme already renders Keycloak's WebAuthn/passkey authentication pages through
`DefaultPage`. Enable the feature in the Keycloak realm that uses this theme:

1. Go to **Authentication** > **Flows** and copy the **Browser** flow.
2. In the copied flow, add the **Passkeys Conditional Authenticator** execution
    to offer passkey sign-in next to the password form. Add the **WebAuthn
    Passwordless Authenticator** execution to complete passwordless sign-in
    (or use **WebAuthn Authenticator** when passkeys are a second factor).
3. Set the appropriate execution requirement, then bind the copied flow as the
    realm's **Browser Flow** under **Authentication** > **Bindings**.
4. Configure **WebAuthn Passwordless Policy** under **Realm settings** >
    **Authentication**. For passkeys, require a user-verifying authenticator and
    use a HTTPS realm URL in production.

When the configured flow reaches the passkey execution, Keycloak serves the
`webauthn-authenticate` page and this theme invokes the browser's passkey prompt.

# How to customize the theme

[Documentation](https://docs.keycloakify.dev/css-customization)

# Building the theme

You need to have [Maven](https://maven.apache.org/) installed to build the theme (Maven >= 3.1.1, Java >= 7).  
The `mvn` command must be in the $PATH.

-   On macOS: `brew install maven`
-   On Debian/Ubuntu: `sudo apt-get install maven`
-   On Windows: `choco install openjdk` and `choco install maven` (Or download from [here](https://maven.apache.org/download.cgi))

```bash
npm run build-keycloak-theme
```

Note that by default Keycloakify generates multiple .jar files for different versions of Keycloak.  
You can customize this behavior, see documentation [here](https://docs.keycloakify.dev/features/compiler-options/keycloakversiontargets).

# Initializing the account theme

```bash
npx keycloakify initialize-account-theme
```

# Initializing the email theme

```bash
npx keycloakify initialize-email-theme
```

# GitHub Actions

The starter comes with a generic GitHub Actions workflow that builds the theme and publishes
the jars [as GitHub releases artifacts](https://github.com/keycloakify/keycloakify-starter/releases/tag/v10.0.0).  
To release a new version **just update the `package.json` version and push**.

To enable the workflow go to your fork of this repository on GitHub then navigate to:
`Settings` > `Actions` > `Workflow permissions`, select `Read and write permissions`.
