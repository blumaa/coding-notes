## Backend

To run server with alternative db
`DATABASE_NAME_DEVELOPMENT=localyze_e2e rails s`

to change the name of db in postico

`ALTER DATABASE “db/localyzeapp_development” RENAME TO “localyzeapp_e2e”`

### Manually triggering a sync

`GloMo::TalentOverview::SyncService.call(279)` or `GloMo::TalentOverview::SyncService.call!(279)`

`FrontUser.pluck(:id).each { |talent_id| GloMo::TalentOverview::SyncWorker.perform_async(talent_id) }`

just one command to run them all:

```
bin/dev
```

This uses Foreman to run the backend, frontend, and Sidekiq, altogether.

## Coverage

`yarn test:coverage`

that will create a `coverage` folder

then you have a `lcov-report` folder inside this one, open the `index.html` and you can explore

## Custom Branding

How to upload a logo to staging

``file_url = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png"`

`file_url="[https://drive.google.com/file/d/1m-_mlrJszCqmFNVDPwpU-_k-PIJtcHWP/view?usp=share](https://drive.google.com/file/d/1m-_mlrJszCqmFNVDPwpU-_k-PIJtcHWP/view?usp=share_link)"`

`file = HTTParty.get(file_url)
File.open('logo.png', 'wb') { |fo| fo.write file }`

`logo = File.open('logo.png', 'rb')`

`comp = Company.first
comp.update(logo: logo)`

## Cypress

### Adjust Settings

in `cypress.config.js`

```jsx
baseUrl: 'http://localhost:3001',
```

in `environments.js`

```jsx
caseManager: {
      email: 'admin@localyzea.de',
      password: '12345678Aa!',
    },
```

### Running the tests

To run the cypress UI: `./node_modules/.bin/cypress open`

You can run the tests live in the browser by adding the `--head` or you can just enter the command 

Alternatively, you can run the tests with `yarn cypress run`

Run and debug Single Cypress test

`yarn cypress run --spec cypress/e2e/variablesEditor/variablesEditor.spec.ts --no-exit -b chrome --headed`

Run and debug Single Cypress test

`yarn e2e —spec cypress/integration/talent/login.spec.ts --no-exit`

In order run the e2e tests, you have to seed the rails env with test data

`RAILS_ENV=test bin/rails db:seed`

sometimes you have to migrate and then run this command again

then run the rails env with test

`RAILS_ENV=test bin/rails s`

If it is still not working, try to build the FE with `yarn build`

Then you can run `yarn cypress open`

## Evaluation and Assessment

### Tool for Improving work flow through a project.

1. Create a rubric together that defines a scale or spectrum.
    1. e.g. Excellent work flow vs. not so good working flow
    2. Could have three through ten points.
        1. The number of points is defined during the creation of the tool.
        2. You come up with examples of what you want to strive towards vs what you want to avoid
        3. What do these things look like? Feel like? Sound like? etc.
2. Go through a project, keeping this scale or spectrum in mind.
3. After the project, use the tool with your partner or group. Everyone fills out a rubric for their self.
    1. How well did your team do this time? What makes you say that?
    2. What can be improved next time?
        1. Make concrete points. Does this change the way the rubric is designed? Do you need to adjust the rubric in order to tune into a different outcome? What’s not working or useless from the rubric?

## Frontend Masters

## Quotes

- Have a problem before you solve a problem.
- The juice isn’t worth the squeeze
- Test functionality, not implementation
- Get into the habit of deleting old tests

# Command Line / Linux

### cli

- `ctl + R` reverse search
- `tail ~/.zsh_history`
- CTRL + A – takes you to the beginning of the line
- CTRL + E – takes you to the end of the line
- CTRL + K – "yank" everything after the cursor
- CTRL + U – "yank" everything before the cursor
- CTRL + Y - "paste" (paste in quotes because it doesn't actually go into your system clipboard) everything you yanked
- CTRL + L - clear the screen

## Git

Add to current commit and don’t change title

`git commit --amend --no-edit`

How to rebase

`git rebase from origin/main`

`git rebase -i HEAD~10`

How to squash commits

`git reset --soft HEAD~1`

`git commit specific files`

`git push --force-with-lease`

when editing a commit

`git commit --amend`

`git commit --continue`

see all commits for a branch

`git log --oneline`

Or, git shortlog, which groups commits by user, again showing just the subject line for concision

How to update Main Branch

`git fetch`

`git rebase origin/main`

git rebase origin/main (puts most recent changes on main before your current changes/commits)

git push --force-with-lease (necessary after we rebase or modify our git history)

### interactive rebase

git rebase -i HEAD~10

git reset --soft HEAD~1  (used to split our current commit, the soft option keeps the files so we can used them to make more commits)

How change from https to ssh:

`git remote **set**-url origin git@github.com:{USERNAME}/{PROJECTNAME}.git`

## Heroku Consoles

Access Rails console from Staging

`heroku run rails c -a localyzestaging`

————————————————————————————

Access Rails console from Prod

`heroku run rails c -a localito-production`

## Javascript Theory

# Currying

https://builtin.com/software-engineering-perspectives/currying-javascript

# **WHAT IS CURRYING IN JAVASCRIPT?**

Currying in JavaScript transforms a function with multiple arguments into a nested series of functions, each taking a single argument. Currying helps you avoid passing the same variable multiple times, and it helps you create a higher order function.

## Jest and Memory Leakage

You can use workerIdleMemoryLimit on jest config to limit the max of allocated memory (I used 512MB) to discover which test was stuck. And  yarn test --logHeapUsage  to check the memory consumption per test file.

## LAWS

Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure.

Conway's law

A complex system that works is invariably found to have evolved from a simple system that worked. A complex system designed from scratch never works and cannot be patched up to make it work. You have to start over with a working simple system.

Gall’s Law

## Linting

### Update single file with Prettier

`yarn prettier --write 
/Users/jvaladas/Localyze/Backend/client/src/pages/viewsNew/common/InternationalProfile/InternationalDetails/InternationalDetailsContext.tsx`

## Rails

Testing

Parallel groups specs into smaller amounts

`rake parallel:prepare`

`rake parallel:rspec`

## VIM

`_` goes to the beginning

`$`goes to the end

`0`goes to the beginning character (0 character)

`d$` move from your cursor to the end

`f(` forward to the character (in this case parenthisis), use `f`+`;`to go to character and repeat it

`F(`back to the character

`t(` until just before the character

`T(`back until the just before character

`,`backward

`;`forward

`dt(`delete up to open parenthesis

Search and replace:

1. Execute a regular search with `/`.
2. Use the keystroke `cgn` on the first result to replace it.
3. Type `n` or `N` to go to the next result.
4. Use `.` to replace the occurrence with the same replacement, or go to the next result if you want to keep it.

What’s this `cgn` keystroke, you may ask? What does it mean? If you read `:help gn`, you’ll see that `gn` is the same as `n`, except that it will start Visual mode and select the occurrence. We just do a change (`c`) on the next (selected) searched occurrence. From there, you can imagine that keystrokes like `cgN` or `dgn` will work as well.

`csw"`- vim-surround, surround current word with quotes

`ysiw"`- vim-surround, surround current word with quotes

`ctl-v` then go down or up, it will select the current character vertically. Then press `$A`to insert at the end and replace everything - https://vimtricks.com/p/edit-multiple-lines-at-once-in-vim/

normal mode H toggles dotfiles

normal mode I toggles gitignore

`ctl z` exit vim with saving terminal

`fg` resume vim with same windows

`zz` center vim at your cursor
