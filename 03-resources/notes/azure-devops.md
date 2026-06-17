---
mocs:
    - "[[public-notes/03-resources/devops.moc.md|DevOps & Cloud]]"
tags:
    - dev/devops
---

+ **Azure Boards**: Implement an agile methodology, assign user stories, etc.
+ **Azure Repos**: Source Control Management, in private git repos
+ **Azure Pipelines**: Code -> Test -> Package (source code into a single ==artifact==: deliverable that we can deploy on an environment) -> Deploy (automating CI / CD)
	+ **Task**: Are pre-created scripts, which you can use as a convenience
	+ **Job**:
		+ represents an execution boundary for a group of multiple steps (scripts), if you only have 1 job, you don't need to specify it
		+ Each job is executed in a different environment (machine / agent)
		+ Other use-case is run multiple test in paralell
	+ **agent** is computing infrastructure with agent software installed on it, an agent is selected from a agent pool
+ **Azure Artifacts**: files produced by the build process of the source code
	+ you can store the artifacts produced by the CI Pipeline and easily connecting and pushing to Azure Artifcats
	+ a moder aproach is use build docker images instead artifacts
![[Pasted image 20250113225807.png]]
+ push to (docker) repository
![[Pasted image 20250113230053.png]]

We can view each of this as different stages


**Template**: We can use a template to reuse the same pipeline across multiple projects
+ You can create templates for jobs, stagtes or steps (store them in github templates)
**Azure Test Plans**: Centralize test of the results of test (automate or manual)
+ Functional Tests
+ Integration Tests
+ Performance Tests
