## Stackpoint

+ Azure `spceastus` resource group

```
Inbound security rules
Priority	Name	Port	Protocol	Source	Destination	Action	
1010	ssh-inbound	22	TCP	Any	Any	Allow	…
1020	http-inbound	80	TCP	Any	Any	Allow	…
1030	https-inbound	443	TCP	Any	Any	Allow	…
1040	https-apiserver	6443	TCP	Any	Any	Allow	…
1050	kubenetes-nodeport	30000-32767	TCP	Any	Any	Allow	…
1060	dns-inbound	53	TCP	VirtualNetwork	VirtualNetwork	Allow	…
1070	http-insecure-apiserver	8080	TCP	VirtualNetwork	VirtualNetwork	Allow	…
1080	etcd-inbound-4001	4001	TCP	VirtualNetwork	VirtualNetwork	Allow	…
1090	etcd-inbound	2379-2380	TCP	VirtualNetwork	VirtualNetwork	Allow	…
1100	kubelet	10250	TCP	VirtualNetwork	VirtualNetwork	Allow	…
1110	deny-inbound	0-65535	TCP	Any	Any	Deny	…
65000	AllowVnetInBound	Any	Any	VirtualNetwork	VirtualNetwork	Allow	…
65001	AllowAzureLoadBalancerInBound	Any	Any	AzureLoadBalancer	Any	Allow	…
65500	DenyAllInBound	Any	Any	Any	Any	Deny	…
Outbound security rules
Priority	Name	Port	Protocol	Source	Destination	Action	
1120	any-outbound	Any	Any	Any	Any	Allow	…
65000	AllowVnetOutBound	Any	Any	VirtualNetwork	VirtualNetwork	Allow	…
65001	AllowInternetOutBound	Any	Any	Any	Internet	Allow	…
65500	DenyAllOutBound	Any	Any	Any	Any	Deny	…
```

Outbound security rules
Priority
	
Name
	
Port
	
Protocol
	
Source
	
Destination
	
Action
	
1120
	
any-outbound
	
Any
	
Any
	
Any
	
Any
	
Allow
	…
65000
	
AllowVnetOutBound
	
Any
	
Any
	
VirtualNetwork
	
VirtualNetwork
	
Allow
	…
65001
	
AllowInternetOutBound
	
Any
	
Any
	
Any
	
Internet
	
Allow
	…
65500
	
DenyAllOutBound
	
Any
	
Any
	
Any
	
Any
	
Deny
	…

```
https://api.stackpoint.io/cluster/7768/kubeui/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard/#!/role?namespace=_all
```
