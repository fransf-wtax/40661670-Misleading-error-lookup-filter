# Case #40661670 - Misleading error message "Invalid lookup filter: Syntax error. Found 'end of formula' "

This is a minimal project to show misleading error message shown when pushing code to a scratch org for a project that has a look field with a lookup filter that references a missing record type on the target object.


# To reproduce

Create a new scratch org:

    sfdx force:org:create -f config/project-scratch-def.json -d 1 -s

Push the source:

    sfdx force:source:push

An error is shown:

    *** Deploying with REST ***
    Job ID | 0Af7E00001XoyWRSAZ
    SOURCE PROGRESS | █████████████████████████████████████░░░ | 13/14 Components
    TYPE   PROJECT PATH                                                              PROBLEM
    ─────  ────────────────────────────────────────────────────────────────────────  ─────────────────────────────────────────────────────────────────────
    Error  force-app/main/default/objects/Product2/fields/Account__c.field-meta.xml  Invalid lookup filter: Syntax error.  Found 'end of formula' (149:13)
    ERROR running force:source:push:  Push failed.


When the record type does exist, the push is successful. This can be shown by replacing `sfdx-project.json` by `sfdx-project-with-suppliers.json` and retrying the `sfdx force:source:push` again.

