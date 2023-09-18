# Assign policies to Projects

After you apply [Project attributes](../../snyk-admin/introduction-to-snyk-projects/project-attributes.md) to your Projects, you can create policies that apply to those attributes. Projects and policies are linked based on the attributes that have the policy applied.

{% hint style="info" %}
Policies applied to Project attributes always take precedence over policies applied to Organizations.
{% endhint %}

A policy can be applied to one or multiple Project attributes, but only one policy can be applied to a set of attributes. For example, if there is a policy applied to `Critical`**,** `Production`,`Frontend`, you cannot create another policy that is applied _only_ to these exact attributes.

{% hint style="info" %}
Policies applied to Project attributes affect the CLI command `snyk monitor`, assuming it runs on a CLI Project that has Project attributes assigned. Project attributes applied to policies do not affect `snyk test`.
{% endhint %}

## Apply a policy to Project attributes and remove a policy

To apply a policy to an attribute, in the attribute selector panel, check the box for the attribute to which you want to apply the policy.

To remove a policy from an attribute, uncheck the box next to the attribute from which want to remove the policy.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_1.20.42_pm.png" alt="Add attributes to policies"><figcaption><p>Add attributes to policies</p></figcaption></figure>

</div>

<figure><img src="../../.gitbook/assets/Screenshot 2023-07-28 at 17.28.18.png" alt="Attribute selector panel"><figcaption><p>Attribute selector panel</p></figcaption></figure>

{% hint style="info" %}
You can create and save a policy where no attributes are selected, for example, if you have not yet decided the attributes to which the policy should be applied. A policy cannot apply to Projects if all attributes are left blank.
{% endhint %}

## Assign Projects to policies

To have a policy assigned, a Project must have all the attributes listed on the policy, that is, to which the policy is applied. The Project can also have attributes that are not listed on the policy.

For example, if you have a policy applied to `Critical`, `External`, and `Frontend`, this policy is assigned to Projects that have the same attributes, but not to a Project with the attributes `Critical` and `External` only.

An example policy follows. It is applied to an attribute in the **Business Criticality** section, `Critical`, and to attributes in the **Environment** section,  `Frontend` and `External`.

<figure><img src="../../.gitbook/assets/Screenshot 2023-07-28 at 17.44.45.png" alt="Sample policy"><figcaption><p>Sample policy</p></figcaption></figure>

The following Project has the attributes `Frontend`, `External`, and `Critical`. Thus the Project will inherit the policy, that is, the policy is assigned to this Project.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.26.02_pm.png" alt="Project inheriting a policy"><figcaption><p>Project inheriting a policy</p></figcaption></figure>

</div>

The following Project will not inherit the policy, because the Project lacks the `External` environment attribute.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.29.03_pm.png" alt="Project not inheriting a policy"><figcaption><p>Project not inheriting a policy</p></figcaption></figure>

</div>

## Assign multiple policies to a Project

Multiple policies can be assigned to a Project. For example, you may have a policy applied to the attributes `Critical` and `External` and another policy applied to the attributes `Critical` and `Production`. If you have a Project with the attributes `Critical`, `External` and `Production`,  both policies are assigned.

When multiple policies are assigned to a Project, the order of the policies on the policy manager page determines precedence. The policy closest to the top of the list takes precedence over other assigned policies after it. To change the order of policies, either drag and drop the policies into the order you want or use the three dots on the right-hand side to move the policy up or down in the list.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2021-03-11_at_12.51.25_pm.png" alt="Change policy order"><figcaption><p>Change policy order</p></figcaption></figure>

</div>