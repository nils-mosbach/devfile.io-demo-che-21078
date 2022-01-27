# devfile.io Demo Workspace for che#21078

Relates to https://github.com/eclipse/che/issues/21078#issue-1115165842: Che-Operator - Reconciling DevWorkspaceRouting - NPE

## Che-Operator throws the following log:

```
2022-01-27T09:22:00.772Z	INFO	Binary info 	{"Go version": "go1.16.12"}
2022-01-27T09:22:00.772Z	INFO	Binary info 	{"OS": "linux", "Arch": "amd64"}
2022-01-27T09:22:00.772Z	INFO	Address 	{"Metrics": ":60000"}
2022-01-27T09:22:00.772Z	INFO	Address 	{"Probe": ":6789"}
2022-01-27T09:22:00.772Z	INFO	Operator is running on 	{"Infrastructure": "Kubernetes"}
I0127 09:22:01.824177       1 request.go:668] Waited for 1.046831901s due to client-side throttling, not priority and fairness, request: GET:https://10.43.0.1:443/apis/snapshot.storage.k8s.io/v1alpha1?timeout=32s
time="2022-01-27T09:22:03Z" level=info msg="Limit cache by selector: app.kubernetes.io/part-of=che.eclipse.org"
2022-01-27T09:22:05.281Z	INFO	controller-runtime.metrics	metrics server is starting to listen	{"addr": ":60000"}
time="2022-01-27T09:22:07Z" level=info msg="Use 'terminationGracePeriodSeconds' 20 sec. from operator deployment."
time="2022-01-27T09:22:07Z" level=info msg="Set up process signal handler"
2022-01-27T09:22:09.819Z	INFO	setup	DevWorkspace support enabled.
2022-01-27T09:22:09.819Z	INFO	setup	starting manager
I0127 09:22:09.819701       1 leaderelection.go:243] attempting to acquire leader lease dev-studio/e79b08a4.org.eclipse.che...
2022-01-27T09:22:09.819Z	INFO	controller-runtime.manager	starting metrics server	{"path": "/metrics"}
I0127 09:22:52.496775       1 leaderelection.go:253] successfully acquired lease dev-studio/e79b08a4.org.eclipse.che
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.namespace	Starting EventSource	{"reconciler group": "", "reconciler kind": "Namespace", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.checlusterrestore-controller	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterRestore", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.namespace	Starting EventSource	{"reconciler group": "", "reconciler kind": "Namespace", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.checlusterrestore-controller	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterRestore", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.checlusterrestore-controller	Starting Controller	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterRestore"}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.namespace	Starting EventSource	{"reconciler group": "", "reconciler kind": "Namespace", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.namespace	Starting EventSource	{"reconciler group": "", "reconciler kind": "Namespace", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.namespace	Starting Controller	{"reconciler group": "", "reconciler kind": "Namespace"}
2022-01-27T09:22:52.496Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checlusterbackup-controller	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterBackup", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checlusterbackup-controller	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterBackup", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checlusterbackup-controller	Starting Controller	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterBackup"}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting Controller	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster"}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting EventSource	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting EventSource	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting EventSource	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting EventSource	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting EventSource	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting", "source": "kind source: /, Kind="}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting Controller	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting"}
2022-01-27T09:22:52.497Z	INFO	controller-runtime.manager.controller.checluster	Starting Controller	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster"}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.checlusterrestore-controller	Starting workers	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterRestore", "worker count": 1}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.checlusterbackup-controller	Starting workers	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheClusterBackup", "worker count": 1}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.checluster	Starting workers	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "worker count": 1}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.devworkspacerouting	Starting workers	{"reconciler group": "controller.devfile.io", "reconciler kind": "DevWorkspaceRouting", "worker count": 1}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.namespace	Starting workers	{"reconciler group": "", "reconciler kind": "Namespace", "worker count": 1}
2022-01-27T09:22:52.668Z	INFO	controller-runtime.manager.controller.checluster	Starting workers	{"reconciler group": "org.eclipse.che", "reconciler kind": "CheCluster", "worker count": 1}
2022-01-27T09:22:52.669Z	INFO	controllers.DevWorkspaceRouting	Reconciling DevWorkspaceRouting	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
2022-01-27T09:22:52.669Z	INFO	controllers.DevWorkspaceRouting	Adding Finalizer for the DevWorkspaceRouting	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
2022-01-27T09:22:52.770Z	INFO	sync	Creating a new object	{"kind": "v1.ConfigMap", "name": "workspace102b7ed75a3a493f-route", "namespace": "dev-studio"}
2022-01-27T09:22:52.805Z	INFO	sync	Creating a new object	{"kind": "v1.ConfigMap", "name": "workspace102b7ed75a3a493f-route", "namespace": "che-workspace-nm-zsobsb"}
2022-01-27T09:22:52.868Z	INFO	controllers.DevWorkspaceRouting	Created object	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "kind": "v1.Service", "name": "workspace102b7ed75a3a493f-service"}
2022-01-27T09:22:52.868Z	INFO	controllers.DevWorkspaceRouting	Services not in sync	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
2022-01-27T09:22:52.884Z	INFO	controllers.DevWorkspaceRouting	Reconciling DevWorkspaceRouting	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
2022-01-27T09:22:52.901Z	INFO	controllers.DevWorkspaceRouting	Created object	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "kind": "v1.Ingress", "name": "workspace102b7ed75a3a493f-logging-grafana-4900-grafana"}
2022-01-27T09:22:52.941Z	INFO	controllers.DevWorkspaceRouting	Created object	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "kind": "v1.Ingress", "name": "workspace102b7ed75a3a493f-nodejsdev-3000-nodejs"}
2022-01-27T09:22:52.941Z	INFO	controllers.DevWorkspaceRouting	Ingresses not in sync	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
2022-01-27T09:22:52.957Z	INFO	controllers.DevWorkspaceRouting	Reconciling DevWorkspaceRouting	{"Request.Namespace": "che-workspace-nm-zsobsb", "Request.Name": "routing-workspace102b7ed75a3a493f", "devworkspace_id": "workspace102b7ed75a3a493f"}
panic: runtime error: invalid memory address or nil pointer dereference
[signal SIGSEGV: segmentation violation code=0x1 addr=0x10 pc=0x167eb56]
goroutine 1353 [running]:
github.com/devfile/devworkspace-operator/pkg/config.ExperimentalFeaturesEnabled(...)
	/che-operator/vendor/github.com/devfile/devworkspace-operator/pkg/config/sync.go:90
github.com/devfile/devworkspace-operator/pkg/provision/sync.printDiff(0x1faf4b0, 0xc000b6f380, 0x1faf4b0, 0xc000b6f500, 0x1f91db8, 0xc000597db0)
	/che-operator/vendor/github.com/devfile/devworkspace-operator/pkg/provision/sync/sync.go:128 +0x36
github.com/devfile/devworkspace-operator/pkg/provision/sync.SyncObjectWithCluster(0x1faf4b0, 0xc000b6f380, 0x1f9df58, 0xc0006a8fa0, 0x0, 0x0, 0xc0009a5d50, 0x1f91db8, 0xc000597db0, 0x1f87f88, ...)
	/che-operator/vendor/github.com/devfile/devworkspace-operator/pkg/provision/sync/sync.go:69 +0x487
github.com/devfile/devworkspace-operator/controllers/controller/devworkspacerouting.(*DevWorkspaceRoutingReconciler).syncIngresses(0xc0007126c0, 0xc001324600, 0xc001480300, 0x2, 0x2, 0x1, 0xc000694c80, 0x1, 0x1, 0x0, ...)
	/che-operator/vendor/github.com/devfile/devworkspace-operator/controllers/controller/devworkspacerouting/sync_ingresses.go:58 +0x3d1
github.com/devfile/devworkspace-operator/controllers/controller/devworkspacerouting.(*DevWorkspaceRoutingReconciler).Reconcile(0xc0007126c0, 0x1f87ff8, 0xc00089c3f0, 0xc000c1aed0, 0x2d, 0xc000c1aea0, 0x21, 0xc00089c3f0, 0xc000d00000, 0x1b8e5a0, ...)
	/che-operator/vendor/github.com/devfile/devworkspace-operator/controllers/controller/devworkspacerouting/devworkspacerouting_controller.go:206 +0x11a5
sigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).reconcileHandler(0xc0003d6000, 0x1f87f50, 0xc000712c00, 0x1b354a0, 0xc000158160)
	/che-operator/vendor/sigs.k8s.io/controller-runtime/pkg/internal/controller/controller.go:298 +0x30d
sigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).processNextWorkItem(0xc0003d6000, 0x1f87f50, 0xc000712c00, 0xc000e9c700)
	/che-operator/vendor/sigs.k8s.io/controller-runtime/pkg/internal/controller/controller.go:253 +0x205
sigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).Start.func2.2(0xc0008d0010, 0xc0003d6000, 0x1f87f50, 0xc000712c00)
	/che-operator/vendor/sigs.k8s.io/controller-runtime/pkg/internal/controller/controller.go:214 +0x6b
created by sigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).Start.func2
	/che-operator/vendor/sigs.k8s.io/controller-runtime/pkg/internal/controller/controller.go:210 +0x425
```
