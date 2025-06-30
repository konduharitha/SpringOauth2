
## Spring Security with OAuth2: Google and GitHub Login Integration

This project demonstrates the integration of **Google and GitHub login capabilities** into a Spring Boot application using Spring Security's OAuth2 client. The primary goal is to offer a **convenient and familiar login experience** for users by leveraging established third-party authorisation servers to verify identity.

**Key aspects of this implementation include:**

*   **Delegated Authentication**: Instead of managing traditional username/password authentication, the application delegates user verification to trusted services like Google and GitHub.
*   **Core Dependencies**: The project uses Spring Boot with `spring-web` and `oauth2-client` dependencies. Notably, `oauth2-client` automatically includes necessary Spring Security modules.
*   **Custom Security Configuration**: A custom `SecurityConfig` class is implemented to override default Spring Security behaviour, enabling `oauth2Login` and ensuring all requests are authenticated.
*   **OAuth2 Client Registration**: Client registration details for Google and GitHub (including `client-id` and `client-secret`) are configured in `application.properties`.
    *   **Google Credentials**: Obtained from the **Google Cloud Console**, requiring an "OAuth client ID" for a "Web application" and setting an "Authorized redirect URI" (e.g., `http://localhost:8000/login/oauth2/code/google`).
    *   **GitHub Credentials**: Sourced from **GitHub Developer Settings** under "OAuth Apps", where a "Callback URL" (e.g., `http://localhost:8000/login/oauth2/code/github`) is configured.
*   **Seamless User Experience**: Upon correct configuration, the application presents both Google and GitHub login options. Once a user authenticates via either platform, they remain logged in, with the application utilising the token provided by the respective OAuth2 provider.