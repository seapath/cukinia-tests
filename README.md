# cukinia-tests

This repository is a part of the [SEAPATH](https://www.lfenergy.org/projects/seapath/) project.
It contains Cukinia's tests, which can be run on SEAPATH machines.
These tests can be run and deployed using the SEAPATH ansible playbook:
* [test_deploy_cukinia.yaml](https://github.com/seapath/ansible/blob/debian-main/playbooks/test_deploy_cukinia.yaml "test_deploy_cukinia.yaml") to install Cukinia on a machine
* [test_deploy_cukinia_tests.yaml](https://github.com/seapath/ansible/blob/debian-main/playbooks/test_deploy_cukinia_tests.yaml "test_deploy_cukinia_tests.yaml") to deploy tests
* [test_run_cukinia.yaml](https://github.com/seapath/ansible/blob/debian-main/playbooks/test_run_cukinia.yaml "test_run_cukinia.yaml") to run the tests

Tests are installed in /etc/cukinia. They can be run manually with the cukinia command:
* cukinia /etc/cukinia/cukinia-observer.conf run all tests for observers including security tests.
* cukinia /etc/cukinia/cukinia-hypervisor.conf run all tests for hypervisors including security tests.
* cukinia /etc/cukinia/cukinia-sec.conf run security tests only.
* cukinia /etc/cukinia/cukinia-cluster.conf run cluster tests.
* cukinia /etc/cukinia/cukinia-sec-future.conf run security tests which actually failed on SEAPATH (not yet implemented).
* cukinia /etc/cukinia/cukinia-all.conf run all tests.

## Pull request test

A small test scenario is run on every pull request. It just checks that the commits of the pull request have been tested on the complete CI on [seapath/ansible](git@github.com:seapath/ansible.git)
To contribute to this cukinia-tests repository, the workflow is :
- First open a pull request on seapath/ansible that bump the submodule revision to the last commit of your pr.
- When the CI is good, merge your ansible pull request.
- Relaunch test "certify-commit" Github Action on cukinia-tests, it should pass now.
- Merge your cukinia-tests pull request.
