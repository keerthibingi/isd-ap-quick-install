# isd-ap-quick-install
Quick install for ISD Services only.


To experience ISD quickly, you can install it and deploy your applications. Note that the instructions below are intended to get you started quickly and try out ISD functionality. This is not suitable for production or any environment where security is a concern.
To begin installation, you'll need a Kubernetes cluster  (with 2 nodes with 32GB RAM each) and kubectl set-up.

**This is the ISD Autopilot which supports only for Argo**.

Run the following commands (copy paste in a terminal window)

      kubectl -n opsmx-autopilot apply -f https://raw.githubusercontent.com/OpsMx/isd-ap-quick-install/main/ap-without-argo/ap-quickinstall.yaml

- **Create opsmx11 secret:**

   Below Secret need to be created Please updated the password and create a secret

      kubectl create secret docker-registry opsmx11-secret --docker-server=docker.io --docker-username=opsmx11 --docker-password=xxxxx --docker-email=saiteja.katabhatina@opmx.io -n opsmx-autopilot

WAIT for about 10-15 min, depending on network speed.
It is normal for some pods to go into error/crashloop before stabilising.

Check the status of the pods by executing this command:\

      kubectl -n opsmx-autopilot get po

Once all pods show "Running" or "Completed" status, execute below command:

      kubectl -n opsmx-autopilot  port-forward svc/oea-ui 8080  ## Keep running, it shows messages such as "Forwarding from 127.0.0.1:8080 -> 8080"

Now, open your browser and navigate to http://localhost:8080
Login with username admin and password opsmxadmin123
