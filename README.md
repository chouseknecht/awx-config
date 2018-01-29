# AWX config role

Uses [Tower CLI](https://github.com/ansible/tower-cli) to configure an AWX instance.

This role provides a starting point for defining your AWX configuration (e.g., organizations, users, teams, credentials, etc.) externally from an AWX instance. By keeping the majority of your configuration external, you get the freedom to create and destroy AWX instances, which is great for when you're giving demos, providing training, or you just want to live on the cutting edge of AWX development.

The dataset supported by this role is not fully complete. Here's what's NOT in the supported dataset:

- job templates
- workflow templates
- inventory
- notifications

If you use this role, and you figure out how to add one of the above, please submit a PR. Help is always welcome!

## Options

Ideally you will put all of your data into one or more encrypted var files, using Ansible Vault, and then pass the file(s) into the playbook. If you're not quite sure how Ansible Vault works, check out [the docs here](http://docs.ansible.com/ansible/latest/vault.html).

Below are the data elements currently supported by the role:

awx_host: '' 
> Your host FQDN or IP address

awx_username: admin
> Your AWX admin username

awx_password: password
> Your AWX admin password

awx_verify_ssl: false
> Whether or not to very the AWX host's TLS certs.

organizations: []
> Provide a list of organizations to be created. Each organization will be a map of `key: value` pairs. [See example data file](./awx-example-data.yml) for keys.

teams: []
> Provide a list of teams to be created. Each team will be a map of `key: value` pairs. [See example data file](./awx-example-data.yml) for keys.

credentials: []
> Provide a list of credentials to be created. Each credential will be a map of `key: value` pairs, and each credential type has a different mapping of `inputs`. Check the Tower CLI docs for more info on `inputs`. And for each credential, provide an organization name with which to associate the credential. [See example data file](./awx-example-data.yml) for keys.

users: []
> Provide a list of users to be created. Each user will be a map of `key: value` pairs. For each user, provide a list of team names, and a list of organizations. The user will be associated with the teams and organizations. [See example data file](./awx-example-data.yml) for keys.

projects: []
> Provide a list of projects to be created. Each project will be map of `key: value` pairs. For each project, provide an organization name with which to associate the credential. [See example data file](./awx-example-data.yml) for keys.

## Example playbook and data file

An example playbook is provided [here](./awx-setup.yml), along with an example AWX data file [here](./awx-example-data.yml).

## License

[Apache V2](./LICENSE)
