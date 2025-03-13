# Spring Boot Hello World for OpenShift

A simple Spring Boot application with a hello world endpoint, built with Maven and JDK 17, designed for deployment to OpenShift using Source-to-Image (S2I).

## Prerequisites

- JDK 17
- Maven 3.8+
- OpenShift CLI (oc)

## Building the Application

To build the application locally:

```bash
mvn clean package
```

## Running Locally

To run the application locally:

```bash
mvn spring-boot:run
```

The application will be available at http://localhost:8080

## Deploying to OpenShift using S2I

1. Log in to your OpenShift cluster:

```bash
oc login <your-openshift-url>
```

2. Create a new project or use an existing one:

```bash
oc new-project hello-openshift
```

3. Create a new application using S2I:

```bash
oc new-app --name=hello-openshift java:17~https://your-git-repo-url --context-dir=/ --strategy=source
```

4. Expose the service to create a route:

```bash
oc expose svc/hello-openshift
```

5. Get the route URL:

```bash
oc get route hello-openshift
```

Visit the URL to see your application running on OpenShift.