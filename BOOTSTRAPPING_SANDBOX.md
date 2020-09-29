### Establishing connection between two agents:

1. In first agent go to `Invitations`
1. Click `Create New Invite` button
1. In Invitations list find newly created invitation and expand it
1. Click `Copy` in order to copy Invitation URL to clipboard
1. Open second agent and go to `Connections`
1. Paste Invitation URL and click `+Add` button

### Creating service:

##### In order to create service you will need to define required consent first

1. Go to `Consents`
1. Add Consent label
1. Click `Create` button
1. Fill consent data

##### Create service

1. Go to `Services`
1. Find OCA Schema from repository
1. Select required consent by label
1. Click `Submit` button

### Applying on service

> **IMPORTANT: In order to exchange credentials you need activate public DID in _both_ agents**
> 1. Go to `DIDs`
> 1. Expand any DID
> 1. Click `activate` button
> 1. Repeat it in another agent
1. Go to `Connections`
1. Expand connection with agent on which service you want to apply
1. Click `Apply` button
1. Fill service with your data
1. Click `Apply` button
1. In `Services` you can see list of submitted and pending applications
