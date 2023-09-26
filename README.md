# Org Admin 
Used by both CNCF Staff and Technical Advisory Group community members this repo contains configuration files that are used to administer the cncf-tags org.

## Access Control for repos in the cncf-tags org

Access to repos in the cncf-tag org is governed by an application called CLOWarden.

CLOWarden periodically reads the access.yaml file in this repo and uses that file as the desired-state of repository acess.

### How CLOWarden works
In access.yaml, you can add a GitHub profile along with the required GitHub Access to a repo and then CLOWarden will grant that access in this repo.

Teams can also described as groups of GitHub Profiles and also groups of sub-teams

access.yaml is taken by CLOWarden as the desired state describing who has access to the repos in cncf-tags

Periodically, CLOWarden checks the repos and if access has been granted using another means but that access has not been recorded in access.yaml then CLOWarden will act to restore the access described in access.yaml

You MUST grant access to repos using access.yaml here. Access granted using settings.yml will be revoked by CLOWarden.

### How can I request access to a cncf-tag repo ?

Submit a pull request that changes access.yaml to add the profiles along with their required access as an entry to your repo.

### I manage a number of repos and multiple teams can I model that using CLOWarden?

Yes! you can create a team that contains GitHub profiles and grant access for the team to multiple repos.

This allows you to create teams that reflect roles within your Advisory Group. 

You can then refer to your named team(s) when granting access to repos.

### Can I model sub-teams?
Yes! A team can be composed of other teams.
