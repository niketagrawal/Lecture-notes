Instructor notes for the Git introduction lesson of the Software Carpentry. 

The teaching style in these lecture notes has been derived from the Software Carpentry. The lecture notes make use of the [Introduction to version control](https://swcarpentry.github.io/git-novice/aio.html) lesson material of software carpentry distributed under the CC By 4.0 license.

### Program

[12:45 PM - 13:00 PM] Opening <br/>
[13:00 PM - 13:20 PM] Creating a repository <br/>
[13:20 PM - 13:40 PM] Tracking changes: Modify, add, commit cycle <br/>
[13:40 PM - 13:50 PM] Break <br/>
[13:50 PM - 13:55 PM] Recap <br/>
[13:55 PM - 14:20 PM] Exploring history <br/>
[14:20 PM - 14:35 PM] Exercise <br/>
[14:35 PM - 14:40 PM] Exercise Q&A in plenum <br/>
[14:40 PM - 14:50 PM] Ignoring things <br/>
[14:50 PM - 15:00 PM] Break <br/>
[15:00 PM - 15:35 PM] Remotes in GitHub <br/>
[15:35 PM - 15:55 PM] Collaboration <br/>
[15:55 PM - 16:00 PM] Break <br/> 
[16:00 PM - 16:20 PM] Conflicts <br/>
[16:20 PM - 16:35 PM] [Optional] Branches
[16:35 PM - 16:40 PM] Summary + where to go from here? <br/>




### 1. Opening [15 min]

- Slides: Agenda, motivation, version control, git, goals, roadmap


### 2. Doing version control locally: Setting up Git + Creating a repository [15 min] [Typealong]

1. Ojectives [1 min]

    - How do I get set up to use Git?
    - Use case description (Python code to convert fahrenheit to celsius) 
    - Where does Git store information?

2. Launch git bash [1 min]

3. Instructor sets up command history [2 min]

    - On the primary terminal: Run the command 
        ```shell
        export PROMPT_COMMAND="history -a;$PROMPT_COMMAND"
        ```
    - In a separate terminal, create an environment variable pointing to the file where the version history will be stored
    - Make an empty directory, initialize with git, or clone the 4TU repository for workshop notes, and switch to a branch
    - In the same terminal as above, run the command 
        ```shell
        tail -n 0 -f ~/.bash_history | tee $FILE
        ```
    - Enable gitautopush to go through without asking for passphrase: start ssh agent with the command eval `ssh-agent.exe`
    - Add and commit the history file and push once (Can I do this in advance?)

4. Configure git [3 min]

When we use Git on a new computer for the first time, we need to configure a few things. Below are a few examples of configurations we will set as we get started with Git:

    - our name and email address,
    - what our preferred text editor is,
    - and that we want to use these settings globally (i.e. for every project).

```shell
git config --global user.name "name"
$ git config --global user.email "email address"
```

Email address private?

5. Create an empty directory [1 min]

```shell
mkdir convert_temperature
cd convert_temperature
```

6. git repository [slide] [1 min]

7. git init [1 min]; explain what git init does

8. git status [1 min] 

9. Evaluate progress [1 min]

10. Summary and Q&A [2 min]


### 3. Tracking changes: Modify, add, commit cycle [20 min]

1. Questions and objectives [1 min]

    - How do I record changes in Git?
    - How do I check the status of my version control repository?
    - How do I record notes about what changes I made and why?

Note: We follow what git tells us to do till step 6. Instructor explains the concepts in step 7.

2. Create a python file named convert_temperature.py with the below code [2 min]

    ```shell
    def fahrenheit_to_celsius(f):
        c = (f - 32.0) * (5.0/9.0)
        return c
    ```

3. git status [1 min]

4. git diff [1 min]

5. git add [1 min]

6. Explain how git records snapshots. Explain Modify, add, commit cycle [slide] [2 min]

7. git commit + commit messages [2 min]

8. git log; Explain commit identifier, HEAD [2 min] 

9. Summarize the above steps [1 min]

10. Progress checkpoint [2 min]

11. Repeat modify, add, commit cycle; add is __name__==__main__ [2 min]

12. Summarize and Q&A [2 min]


****** 10 minutes Break ******


### 4. Exploring history [25 min]

1. Objectives [1 min] 

    - How can I identify old versions of files?
    - How do I review my changes?
    - How can I recover old versions of files?

3. Modify file: alter temperature conversion formula [0.5 min]

4. git diff HEAD temperature.py [1 min]

5. git diff HEAD~2 temperature.py [0.5 min]

6. Recovering changes; recovering from 3 stages: working directory, staged, committed changes. [1 min]

7. git status: git restore options [1 min]

8. Restore file and bring back to same state as before. This is an example for reverting changes that are not staged. [1 min]

9. Make the same change again

10. Stage changes

11. git status -> git restore --staged to revert 

12. do git restore --staged. This is an example of undoing changes that are staged but not committed.

13. make same change again

14. stage the change

15. commit the change

16. git status > shows empty status because nothing to commit or roll back.

17. git log

18. git show -> only way to spot if you did something wrong

19. When to explain HEAD

20. git checkout HEAD~1 convert_temp.py; Note: This operation brings the changes to the point HEAD~1, then you stage and commit them as usual. Note that the earlier commit stays.

21. stage and commit changes

22. git log

23.  Summarize [2 min]

24. (Optional) Quiz in plenum


### Exercise [15 min]

Link to exercise google doc: https://docs.google.com/presentation/d/17vM2uc_wvCcw7mVMqsNud71K_QZTlcXM4rD2DygkAtk/edit#slide=id.p


### Remotes in GitHub [25 min]

1. Objectives and questions [1 min]

    - How do I share my changes with others on the web?
    - Explain what remote repositories are and why they are useful.
    - Push to or pull from a remote repository.

2. Explain where remote repository fit in the scope of things using a picture (slide 25) [2 min]

3. Explain GitHub/GitLab [1 min]

4. Objective of typealong: Put our local changes on the internet to share with others. 

3. Create an empty GitHhub repository [1 min]

4. Explain SSH [2 min]

4. Setup SSH [15 min]

Link to instructions: https://docs.github.com/en/authentication/connecting-to-github-with-ssh 

5. Connect the local repository with remote repoitory using git add remote origin command as shown after making the repository on GitHub + renaming branch to 'main' [1 min]

6. New command introduction: Git push [1 min]

7. Summarize [1 min]

Notes:
- Pull before you push
- Remote does not get updated with local changes automatically, you have to manually push your changes
- Keep remote up to date by pushing regularly.


### Collaboration [20 min]

1. Objectives [2 min]

    - How can I use version control to collaborate with other people? 

Version control with git really shines when used for collaborating. We learned how we can take our work from our computer to a repository on GitHub and others can see and download your code. We will now see how others can also contribute to your code.


2. [Hands-on] Objective of typealong: Contribute changes to someone else's repsitory. [15 min]

For this step, get into pairs. One person will be the “Owner” and the other will be the “Collaborator”.

Plenum exercise:
- Learner adds their neighbor as collaborator on GitHub repository. Instructor shows how to do this via screen share. [2 min]
- Collaborator clones the repo and make changes, stage and commit locally. [2 min]
- Collaborator pushes changes to Owners github repo. [1 min]
- Owner updates their repository with collaborator's changes using git pull [1 min]
- If time permits, switch roles and repeat. [3 min] 


3. Summarize + Q&A [2 min]
    
Note:Contribute to a repository to which you don't have access to: Not covered today. 


### Conflicts [20 min]

1. Objectives [1 min]

    - What do I do when my changes conflict with someone else’s?

2. Conflict resolution demo [10 min]

    - Instructor adds a helper as a collaborator in the repo.
    - Helper adds an incorrect type hint or wrong print statement in if name==main.
    - Helper pushes the code to owners repo
    - Instructor makes a conflicting change locally and tries to push but the push is blocked due to conflict
    - Instructor follows git's error message and does git pull
    - Instructor sees that a conflict is reported by git and resolves it 
    - Instructor pushes the change

    Tip: Read through SWC episode for correct reproduction of the conflict


3. Takeaway message [5 min]

Git’s ability to resolve conflicts is very useful, but conflict resolution costs time and effort, and can introduce errors if conflicts are not resolved correctly. If you find yourself resolving a lot of conflicts in a project, consider these technical approaches to reducing them:

    - Pull from upstream more frequently, especially before starting new work
    - Use topic branches to segregate work, merging to main when complete
    - Make smaller more atomic commits
    - Push your work when it is done and encourage your team to do the same to reduce work in progress and, by extension, the chance of having conflicts
    - Where logically appropriate, break large files into smaller ones so that it is less likely that two authors will alter the same file simultaneously


### (Optional) Branching [15 min]

1. Motivation for branches: benefits, use cases
2. Branches concept: parallel development line: use a diagram (code refinery diagram is good)
3. Demo: helper makes a feature branch and pushes to the instructor's repository and creates a pull request. Instructor reviews the code and merges the changes.
4. Pull request + code review (good practices)


### Wrap-up [5 minutes]

1. What did we learn today?
2. Key takeaways
3. Where to go next? 
