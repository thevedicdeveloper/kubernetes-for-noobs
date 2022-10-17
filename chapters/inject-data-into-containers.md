<img align="center" src="https://raw.githubusercontent.com/thevedicdev/kubernetes-for-noobs/main/assets/inject-data-into-containers/inject-data-into-containers.jpeg"></img>

<h4 align="center">You Can Read It Anywhere </h4>

<h2 align="center"><a href="https://blogs.thevedicdev.com/kubernetes-for-noobs">Hashnode</a> | <a href="https://dev.to/thevedicdev/kubernetes-for-noobs-425k">Dev.to </a>| <a href="https://medium.com/@thevedicdev/kubernetes-for-noobs-8008ad24e643"> Medium </a> | Hackernoon | <a href="https://github.com/thevedicdev/kubernetes-for-noobs#readme">GitHub</a></h3>

Kubernetes provides 6 different ways to inject your data into the Containers.

1. [Defining Environment Variables for a Container.](#defining-environment-variables-for-a-container)
2. Defining dependant environment variable for a Containers.
3. Defining a command and arguments for a Containers.
4. Passing Pod information to Containers through Environment Variables.
5. Passing Pod infromation to Containers using Volumes.
6. Passsing information to Containers using Secretes.

## Command used for the demonstration

1. Create namespace `<namespace-name>` for the pod.

```bash
kubectl create namespace <namespace-name>
```

2. Creating a Pod using manifest file inside namespace `<namespace-name>`

```bash
kubectl apply -f file-name.yaml --namespace=<namespace-name>
```

3. List the running Pods:

   1. Based on namespace `<namespace-name>`

      ```bash
      kubectl get pod -n=<namespace-name>
      ```

   2. Based on label `<key1>`, `<key2>`,...

      ```bash
      kubectl get pod -l <key1>=<value1>, <key2>=<value2>
      ```

3. Enter into the Container

```bash
kubectl exec -it <container-name>
```

## Defining Environment Variables for a Container

In every programming language there are two fundamental components, `Variables` and `Constants`.

Constant is something whose value cannot be changed during execution of the program whereas, Variables value **may** change during the execution of the program.

There are many different types of Variables and one of them is the [Environment Variable](https://en.wikipedia.org/wiki/Environment_variable). This is a dynamic `named-value` variable whose value is set outside the program.

Containers provide facility to set Environment Variables for the application we are running inside it, and `using Environment Variable we can pass the information/data to our application`.

This is how you set the Environment Variable for an application in the Container. (View [here]( https://raw.githubusercontent.com/kubernetes/website/main/content/en/examples/pods/inject/envars.yaml) the full Pod Template.)

```yaml
env:
- name: FOLLOW_ME_ON_TWITTER
  value: "https://twitter.com/thevedicdev"
- name: FOLLOW_ME_ON_LINKEDIN
  value: "https://www.linkedin.com/in/nishantkantojha/"
- name: FOLLOW_ME_ON_GITHUB
  value: "https://github.com/thevedicdev"
```

<img align="center" src="https://raw.githubusercontent.com/thevedicdev/kubernetes-for-noobs/main/assets/inject-data-into-containers/env-var.png"></img>
Here we are providing three data to the appliation running in our container.
