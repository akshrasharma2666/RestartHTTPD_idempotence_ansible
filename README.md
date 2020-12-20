# RestartHTTPD_idempotence_ansible
New Task !!

Restarting HTTPD Service is not idempotence in nature and also consume more resources suggest a way to rectify this challenge in Ansible playbook.

Here the challenge is - 

Whenever there is some change in configuration file and in the code, the HTTPD apache webserver's service has to be restarted and for this , we generally use "restarted" keyword in the state but if, even there are no changes made to the conf. file, still it restart the webserver(or HTTPD service) by this process whenever we run the playbook. And the challenge is we only wants to restart the service when there are some changes in the code or in conf. file such as changing document root, etc.

Solution: "Use of handlers and notify keyword"
Handlers are just like normal tasks in an Ansible playbook but they run only when if the Task contains a "notify" directive. It also indicates that it changed something.
Sometimes you want a task to run only when a change is made on a machine. For example, you may want to restart a service if a task updates the configuration of that service, but not if the configuration is unchanged. Ansible uses handlers to address this use case. Handlers are tasks that only run when notified. Each handler should have a globally unique name.


