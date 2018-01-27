# AWX config role

Example of using [Tower CLI](https://github.com/ansible/tower-cli) to configure an AWX instance.

## Optons

tower_host: '' 
> Your host FQDN or IP address

tower_username: admin
> Your login username

tower_password: password
> Your login password

tower_verify_ssl: false
> Wether or not to very the Tower hosts TLS certs. Unless

organizations: []
 #- name: ''
 #  description: ''
> Provide a list of organizations to be created. Each organization will be map of `key: value` pairs.

teams: []
 #- name: ''
 #  description: ''
> Provide a list of teams to be created. Each team will be map of `key: value` pairs.

credentials: []
 #- name: '' 
 #  description: '' 
 #  team: Developers
 #  organization: ''
 #  credential_type: ''
 #  # inputs is a text representation of a Yaml data strucuture 
 #  inputs: | 
 #     username: ''
 #     password: ''
> Provide a list of credentials to be created. Each credential will be map of `key: value` pairs. Each credential type has a differenct mapping of `inputs`. Check the Tower CLI docs for more info. For each credential, provide an organization name with which to associate the credential.

users: []
#- username: '' 
#  password: '' 
#  email: ''
#  first_name: 
#  last_name: 
#  organizations: []
#  teams: []
> Provide a list of users to be created. Each user will be map of `key: value` pairs. For each user, provide a list of team names, and a list of organizations. The user will be associated with the organizations and teams.

projects: []
 #- name: '' 
 #  description: '' 
 #  scm_type: ''
 #  scm-url: ''
 #  organization: ''
> Provide a list of projects to be created. Each project will be map of `key: value` pairs. For each project, provide an organization name with which to associate the credential.

## Example playbook

An example playbook is provided [here](./awx-setup.yml), and an example AWX data file is [here](./awx-example-data.yml).

## License

Apache V2
