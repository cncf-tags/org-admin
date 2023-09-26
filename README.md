# Org Admin

Used by both the CNCF Project Team and Technical Advisory Group (TAG) community members, this repo contains configuration information that is used to govern the [cncf-tags][cncf-tag-org-ref] org.

## CLOWarden governs Access Control for repos in the cncf-tags org

Access to repos in the cncf-tag org is governed [CLOWarden][clo-warden-src-ref]

CLOWarden periodically reads the [access-control.yaml][access-control-ref] file in this repo and uses that file as the formally declared desired-state of repository access.

It is the single source of truth that describes who can access what repos and at what level of access (write, read, admin)

### How CLOWarden is configured

In [access-control.yaml][access(control.yam-ref)you can add a GitHub profile along with the required GitHub Access to a repo and then CLOWarden will grant that access in this repo.

Teams can be created using a list of GitHub Profiles and also groups of sub-teams

[access-control.yaml][access-control-ref] is taken by CLOWarden as the desired state describing who has access to the repos in cncf-tags

### How CLOWarden maintains desired state

Periodically, CLOWarden checks permissions granted to repos in this org.

If repo access has been granted using any another means and that access has not been recorded in [access-control.yaml][access-control-ref] then CLOWarden will restore the access described in [access-control.yaml][access-control-ref]

You MUST grant access to repos using [access-control.yaml][access-control-ref] here.

Repo access granted using say an entry in .github/settings.yml will be revoked by CLOWarden if it is not recorded in access-controll.yaml; same applies if access is granted manually;

### How can I request access to a cncf-tag repo ?

Submit a pull request that changes [access-control.yaml][access-control-ref] to add the profiles and/or teams along with their required access as an entry to the repo.

### I manage a number of repos and multiple teams can I model that using CLOWarden?

Yes! you can create a team that contains GitHub profiles and grant access for the team to multiple repos.

This allows you to create teams that reflect roles within your Advisory Group.

You can then refer to your named team(s) when granting access to repos.

### Can I model sub-teams?

Yes! A team can be composed of other teams.

[cncf-tag-org-ref]: https://github.com/cncf-tags/
[access-control-ref]: access-control.yaml
[clo-warden-src-ref]: https://github.com/cncf/clowarden
