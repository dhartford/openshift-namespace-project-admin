# openshift-namespace-project-admin
scripts/tips for non-cluster admins who may be responsible for managing their namespace/projects.

Purge lingering Pods behind the scene that are still there:

  * oc login....
  * oc project <project>
  * for pod in $(oc get pods | grep 'Error\|Evicted\|Completed' | awk '{print $1}'); do oc delete pod --grace-period=1 ${pod}; done

Purge orphaned 'running' pipelines - important, this does not distinguish between active and those that have been orphaned (pipelines that were running, but jenkins got yanked out from underneath):

  * oc login....
  * oc project <project>
  * for pod in $(oc get pods | grep 'Error\|Evicted\|Completed' | awk '{print $1}'); do oc delete pod --grace-period=1 ${pod}; done

