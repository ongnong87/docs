---
title: About the security overview
intro: 'You can view, filter, and sort security alerts for repositories owned by your organization or team in the security overview pages.'
permissions: '{% data reusables.security-overview.permissions %}'
product: '{% data reusables.gated-features.security-overview %}'
redirect_from:
  - /code-security/security-overview/exploring-security-alerts
versions:
  fpt: '*'
  ghae: '*'
  ghes: '*'
  ghec: '*'
type: how_to
topics:
  - Security overview
  - Advanced Security
  - Alerts
  - Dependabot
  - Dependencies
  - Organizations
  - Teams
shortTitle: About the security overview
---

{% ifversion ghes < 3.5 or ghae %}
{% data reusables.security-overview.beta %}
{% endif %}

## About the security overview

{% data reusables.security-overview.about-the-security-overview %} {% ifversion fpt %}For more information, see [the {% data variables.product.prodname_ghe_cloud %} documentation](/enterprise-cloud@latest/code-security/security-overview/about-the-security-overview).{% endif %}

{% ifversion ghec or ghes or ghae %}
The security overview shows which security features are enabled for repositories and consolidate alerts for each feature.

- Risk and coverage information about {% data variables.product.prodname_dependabot %} features and alerts is shown for all repositories. {% ifversion ghes or ghae %}
- Risk and coverage information for {% data variables.product.prodname_GH_advanced_security %} features, such as {% data variables.product.prodname_code_scanning %} and {% data variables.product.prodname_secret_scanning %}, is shown for enterprises that use {% data variables.product.prodname_GH_advanced_security %} and for public repositories.

{% endif %}

For more information, see "[AUTOTITLE](/code-security/dependabot/dependabot-alerts/about-dependabot-alerts#dependabot-alerts-for-vulnerable-dependencies){% ifversion ghes or ghae %}" and{% elsif ghec %}," "[AUTOTITLE](/code-security/secret-scanning/about-secret-scanning#about-secret-scanning-alerts-for-users)" and{% endif %} "[AUTOTITLE](/get-started/learning-about-github/about-github-advanced-security)."

## About filtering and sorting alerts

The security overview provides a powerful way to understand the security of a group of repositories. The views are interactive with filters that allow you to drill into the aggregated data and identify sources of high risk or low feature coverage. As you apply multiple filters to focus on narrower areas of interest, the data across the view changes to reflect your selection. For more information, see "[AUTOTITLE](/code-security/security-overview/filtering-alerts-in-the-security-overview)."

{% ifversion security-overview-alert-views %}
There are also dedicated views for each type of security alert that you can use to limit your analysis to a specific set of alerts, and then narrow the results further with a range of filters specific to each view. For example, in the {% data variables.product.prodname_secret_scanning %} alert view, you can use the `Secret type` filter to view only {% data variables.secret-scanning.alerts %} for a specific secret, like a GitHub {% data variables.product.pat_generic %}.
{% endif %}

{% note %}

**Note:** The security overview displays active alerts raised by security features. If there are no alerts in the security overview for a repository, undetected security vulnerabilities or code errors may still exist.

{% endnote %}

## About the organization-level security overview

{% data reusables.security-overview.beta-org-risk-coverage %}

You can find the security overview on the **Security** tab for any organization that's owned by an enterprise. Each view shows aggregated data that you can drill down into, as you add each filter, the data is updated to reflect the repositories or alerts that you've selected.

The application security team at your company can use the different views for both broad and specific analyses of your organization's security status. {% ifversion security-overview-org-risk-coverage %}For example, the team can use the "Security Coverage" page to monitor the adoption of features across your organization or by a specific team as you rollout {% data variables.product.prodname_GH_advanced_security %}, or use the "Security Risk" page to identify repositories with more than five open {% data variables.secret-scanning.alerts %}.{% else %}For example, they can use the overview page to monitor adoption of features by your organization or by a specific team as you rollout {% data variables.product.prodname_GH_advanced_security %} to your enterprise, or to review all alerts of a specific type and severity level across all repositories in your organization.{% endif %}

Organization owners and security managers for organizations have access to the security overview for their organizations. {% ifversion ghec or ghes > 3.6 or ghae > 3.6 %}Organization members can also access the organization-level security overview to view results for repositories where they have admin privileges or have been granted access to security alerts. For more information on managing security alert access, see "[AUTOTITLE](/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository)."{% endif %}

{% ifversion security-overview-org-risk-coverage %}

### Security Risk view

This view shows data about the repositories affected by different types of security alert.

- Use the **Teams** dropdown menu to show information only for the repositories owned by one or more teams.
- Click **NUMBER affected** or **NUMBER unaffected** in the header for any type of alert to show only the repositories with or without alerts of that type.
- Click any of the descriptions of "Open alerts" in the header to show only repositories with alerts of that type and category. For example, **1 critical** to show the repository with a critical alert for {% data variables.product.prodname_dependabot %}.
- Click **NUMBER Archived** to show only repositories that are archived.
- Click in the search box to show a list of the full set of available filters.

![Screenshot of the "Security Risk" view on the "Security" tab for an organization. Illustrates information and filter options available in the view.](/assets/images/help/security-overview/security-risk-interactive-header.png)


### Security Coverage view

This view shows data about which security features are used by repositories in the organization. You can filter the view to show the repositories of interest using links, a dropdown menu, and a search field.

- Use the **Teams** dropdown to show information only for the repositories owned by one or more teams.
- Click **NUMBER enabled** or **NUMBER not enabled** in the header for any feature to show only the repositories with that feature enabled or not enabled.
- Click **NUMBER Archived** to show only repositories that are archived.
- Click in the search box to show a list of the full set of available filters.

In addition, you can click **{% octicon "gear" aria-hidden="true" %} Security settings** for any repository to enable the security features that have a one-click setup.

![Screenshot of the "Security Coverage" view on the "Security" tab for an organization. Illustrates information and filter options available in view.](/assets/images/help/security-overview/security-coverage-view-single-repo-enablement.png)

{% else %}

### Understanding the main security overview

![Screenshot of the security overview for an organization](/assets/images/help/security-overview/security-overview-org-legacy.png)

For each repository in the security overview, you will see icons for each type of security feature and how many alerts there are of each type. If a security feature is not enabled for a repository, the icon for that feature will be grayed out. In addition, a risk score is calculated for each repository based on its code scanning, Dependabot and secret scanning alerts. This score is in beta and should be used with caution. Its algorithm and approach is subject to change.

| Icon | Meaning |
| -------- | -------- |
| {% octicon "code-square" aria-label="Code scanning alerts" %} | {% data variables.product.prodname_code_scanning_capc %} alerts. For more information, see "[AUTOTITLE](/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)." |
| {% octicon "key" aria-label="Secret scanning alerts" %} | {% data variables.product.prodname_secret_scanning_caps %} alerts. For more information, see "[AUTOTITLE](/code-security/secret-scanning/about-secret-scanning)." |
| {% octicon "hubot" aria-label="Dependabot alerts" %} | {% data variables.product.prodname_dependabot_alerts %}. For more information, see "[AUTOTITLE](/code-security/dependabot/dependabot-alerts/about-dependabot-alerts)." |
| {% octicon "check" aria-label="Check" %} | The security feature is enabled, but does not raise alerts in this repository. |
| {% octicon "x" aria-label="x" %} | The security feature is not supported in this repository. |

{% endif %}

{% ifversion ghec or ghes > 3.4 or ghae > 3.4 %}
## About the enterprise-level security overview

You can find the security overview on the **Code Security** tab for your enterprise. Each overview displays aggregated and repository-specific security information for your enterprise. You can view repositories owned by your enterprise that have security alerts, view all security alerts, or security feature-specific alerts from across your enterprise.

Enterprise owners can view alerts for organizations that they are an owner or a security manager of.{% ifversion ghec or ghes > 3.5 or ghae > 3.5 %} Enterprise owners can join an organization as an organization owner to see all of its alerts in the enterprise-level security overview. For more information, see "[AUTOTITLE](/admin/user-management/managing-organizations-in-your-enterprise/managing-your-role-in-an-organization-owned-by-your-enterprise)."{% endif %}

Organization owners and security managers for organizations in an enterprise have access to the enterprise-level security overview. They can view repositories and alerts for the organizations that they have full access to.
{% endif %}

{% ifversion ghes < 3.7 or ghae < 3.7 %}
## About the team-level security overview

You can find the security overview on the **Security** tab for any team in an organization that's owned by an enterprise.

At the team-level, the security overview displays repository-specific security information for repositories that the team has admin privileges for. For more information, see "[AUTOTITLE](/organizations/managing-user-access-to-your-organizations-repositories/managing-team-access-to-an-organization-repository)."
{% endif %}

## Further reading

- "[AUTOTITLE](/code-security/getting-started/securing-your-repository)"
- "[AUTOTITLE](/code-security/getting-started/securing-your-organization)"
- "[AUTOTITLE](/code-security/adopting-github-advanced-security-at-scale/introduction-to-adopting-github-advanced-security-at-scale)"
{% endif %}
