# iac-lxd-tst-k3s

TST cluster

## Move Kubernetes config file to Gitlab runner

    lxc exec container-adm-glrunner-k2 -- bash -c 'mkdir -p /home/gitlab-runner/.kube'
    lxc file push kube_config.yml container-adm-glrunner-k2/home/gitlab-runner/.kube/config
    lxc exec container-adm-glrunner-k2 -- bash -c 'chown gitlab-runner: /home/gitlab-runner/.kube'
    
Then
    
    lxc exec container-adm-glrunner-k2 -- /bin/bash
    su - gitlab-runner
    kubectl get pods --all-namespaces
