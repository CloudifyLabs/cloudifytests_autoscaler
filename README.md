# cloudifytests_autoscaler



Use following command for auto-scaling the cluster:

    $ helm repo add autoscaler https://kubernetes.github.io/autoscaler
    
    $ helm install my-release autoscaler/cluster-autoscaler \
    --set  'autoDiscovery.clusterName'=cloudifytests \
    --set tolerations[0].key=browsersession \
    --set-string tolerations[0].value=true \
    --set tolerations[0].operator=Equal \
    --set tolerations[0].effect=NoSchedule \
    --set tolerations[0].key=userapp \
    --set-string tolerations[0].value=true \ 
    --set tolerations[0].operator=Equal \
    --set tolerations[0].effect=NoSchedule \
    --set awsRegion=<Your-AWS-region>
    
    
Add metrics server to your cluster using metrics-server/deployment.yaml file.

   $ kubectl apply -f metrics-server/deployment.yaml 
