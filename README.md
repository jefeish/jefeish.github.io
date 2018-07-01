# ![GitHub Logo](/images/githublogo.png) GitHub Enterprise Solutions

# Company: Acme Computers Inc.

## 1. *Acme wants GitHub to help them shrink the large repository to a more manageable size that is performant for common Git operations. The large repo is a project that is high visibility with an aggressive roadmap. They request that we help them within the month.*

*Question to Customer:*
  * Does this repository contain BLOBs ?
  * Can we break this repository up into multiple repositories ?
  * Would [Git Large File Storage](https://git-lfs.github.com/) be an option ?

*Question to GitHub:*
  * Would reducing the commit log be a safe option to reduce repository size ?
  * Public Repositories are limited to 1GB, what's the limit on an Enterprise system ?

## 2. *Acme wants us to help them test GitHub Enterprise performance on a test machine for 20,000 users (their anticipated peak). They have asked you to make them a testing suite to mimic the type of load they will see to be assured GitHub Enterprise can handle the load*

*Question to Customer:*
* For the POC of GitHub Enterprise, is there any hardware infrastructure they are restricted to or would like us to use (Cloud etc.)?

*Question to GitHub:*
* Does the GitHub team have a preferred/recommended load testing tool?
* Do we have an *in-house* team that has experience with GitHub Cluster POCs ?

## 3. *Acme wants you to tell them the best way to move all the other teams, using GitHub Enterprise or other Git solutions, onto their consolidated GitHub Enterprise instance. They have asked you to give them five or six bullet points about how you would approach that initiative, both technically and culturally.*

*Note to GitHub: Given the right tools the goal should be that the Application Teams can perform the migration themselves, the aim is automation and self-service. The GitHub resource should not become a bottleneck to the migration*

Note: The following steps assume the *Consolidated GitHub Enterprise* target environment is setup and ready.
### How To Onboard Teams To A Consolidated GitHub Enterprise

**1. Discuss the new process/infrastructure with the Team**
  (GitHub will provide all required information)
   - [ ] Describe the new GitHub Enterprise CI/CD environment
   - [ ] Explain changes in process (CI/CD) - if any
   - [ ] Address the teams concerns / issues
   - [ ] Provide additional training if required
   - [ ] Agree on a timeline (consider team availability)

**2. Create a GitHub Organization in the Consolidated GitHub Enterprise**
   - [ ] Determine if there is already a GitHub Enterprise organization that would fit the Team or if we need to create a new one

**3. Permission access for the GitHub Enterprise Organization**
   - [ ] Every team member should verify their access (sign off)

**4. Migrate the Teams eligible repositories to the GitHub Enterprise Organization**

   - [ ] Set a migration window for the 'old' repository (at that point no un-committed code)
   - [ ] Remove write access to 'old' repository
   - [ ] Migrate repository

   * Initially all this should be done in sequence, starting with the lowest risk repository first, if there are no issues with the process we can move to bulk or group migration of repositories.

**5. Verify CI/CD tools integration**
   - [ ] Make sure that all required build, test and collaboration tools are still functioning
   - [ ] Request Team sign off after verifying a working CI/CD pipeline (each repository)

**6. Complete the migration - Shutdown the 'old' Repository**
   - [ ] Remove access permissions (write access first), no more commits the 'old' repositories
   - [ ] Remove old repositories after a couple of successful build cycles


<br><br><br><br><br><br>

----
## The section below contains my general migration process and was added for completeness
---
#### General information required from customer:

**Baseline Information**
* What is their current delivery pipeline (CI/CD Tools and Process) ?
* What is/are the current users authentication process(es). ?
  * do users have multiple accounts with different IDs used across GitHub instances?
* Does the customer have different versions of GitHub Enterprise installed, if yes, how many instances and which version ?
* Number of active repositories to be migrated ?
* Customer talks about large repositories, what's the average Repository size ? (a list of all repositories with size would be best)
* Their large repository is ~7 GB,
  * does this contain BLOBs ?
  * can we break this Repo up into multiple Repos ?
  * Would [Git Large File Storage](https://git-lfs.github.com/) be an option for the customer ?

* Customer is asking for a POC for GitHub Enterprise, is there any hardware infrastructure they are restricted to or would like us to use (Cloud etc.)?
* Just to be sure, are there any other non github Version Control Systems to be considered ?

#### Additional information required from GitHub:

* Does the GitHub team have a standard process/guidelines for that kind of customer request ?
  * How do we classify high risk vs low risk repositories ?
* What are the tools that are commonly used by GitHub team members for migrations like this ?
  * Found:
    * [Importing Source Code To GitHub](https://help.github.com/articles/importing-source-code-to-github/)
    * [GitHub Importer](https://blog.github.com/2016-02-11-migrate-your-code-with-the-github-importer/)
    (Any restrictions for GitHub Enterprise on-premise) ?
    * Repository stats [GitHub Developer Rest API](https://developer.github.com/v3/repos/statistics/)


* Does the GitHub team have a preferred load testing tool?
* Do we have an *in-house* team that has experience with GitHub Cluster POCs ?
* Public Repositories are limited to 1GB, what's the limit on an Enterprise system ?

-----

### Standard Pre-Migration Steps:
* Identify repositories eligible for migration
* Gather GitHub installation and repository statistics
* Identify high/low risk repositories to create a migration order
* Discuss the use of GitHub organizations and identify required organizations (assuming not every one is familiar with the Enterprise version)
* Identify all required CI/CD tools currently used with GitHub
* Architect the target GitHub Enterprise infrastructure
  * Identify Clustering / HA requirements
  * Determine Average / Peak load
* Implement the target environment (Consolidated GitHub Enterprise)
* Verify connectivity of the new system with existing CI/CD tools
  * authentication / firewalls ...

## Baseline Inventory Sample

Repository | GitHub Installation | Version | Repo Size | Number of Contributors | Number of Commits | Last Commit | Deployment Frequency | Business Importance (low/medium/high)
--- | --- | --- | --- | --- | --- | --- | --- | --- 
foo | GitHub Enterprise | 2.9.4 | 7 GB | 20 | 30 | 07/09/18 | weekly | medium
| | | | | | | |

