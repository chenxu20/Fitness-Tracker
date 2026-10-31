Build a **mobile-friendly web app for logging workouts and tracking progress**, with the goal of using it during your own gym sessions.

At **5–10 hours per week**, aim for a working app within the first month, then spend another 4–8 weeks improving its testing, deployment, and reliability.

**Keep the first version small**

You should be able to:

- Sign in and access your own workouts.
- Create a routine, such as “Push Day”.
- Start a workout from that routine.
- Record exercises, sets, reps, and weight.
- See your previous performance while entering a set.
- Finish a workout and browse your history.
- View a simple progress chart for an exercise.

For example:

> Open Push Day → see last session’s bench press numbers → record today’s sets → finish workout → review progress.

Leave nutrition, AI coaching, wearables, social features, and offline synchronisation for later.

**Suggested stack**

This follows the technologies already considered in your feature flag plan:

| Part | Choice | Purpose |
|---|---|---|
| Frontend | React + TypeScript | Mobile-friendly interface |
| Backend | Python + FastAPI | API and application logic |
| Database | PostgreSQL | Related workout data and SQL practice |
| Local environment | Docker Compose | Run the API and database consistently |
| CI/CD | GitHub Actions | Automated checks and deployments |
| Cloud | AWS | Host the application and supporting resources |
| Infrastructure | Terraform | Define and reproduce cloud resources |

For the backend deployment, choose **one container hosting approach**, such as ECS with Fargate. Work out the running cost before provisioning it; a small cloud deployment is sufficient for this project.

**Weeks 1–2: Build one complete workout flow**

Sketch three screens: routine list, active workout, and workout history. Design a small database:

```text
User
 ├── Routines → Routine exercises
 └── Workouts → Workout exercises → Sets

Exercise catalogue
```

Keep completed workouts separate from routine templates so editing a routine does not rewrite your history.

Build the ability to start, log, and finish a workout locally. Use a small exercise list that you enter yourself.

**Deliverable:** you can record a real gym session from your phone over your local network.

**Weeks 3–4: Make it usable and deploy it**

Add authentication using an established library or service, restrict records to their owner, and implement routine editing and workout history.

Set up CI to run formatting, linting, and meaningful tests. Deploy the first usable version and add basic error logging.

Test important behaviours:

- Another user cannot read or change your workouts.
- Invalid reps or weights are rejected.
- Repeated submissions do not accidentally duplicate a completed workout.

**Deliverable:** a deployed app that you use for your own workouts.

**Weeks 5–6: Improve it using your experience**

Add previous-session numbers, exercise progress charts, and editing for incorrectly entered sets. Improve the mobile interface based on what feels awkward in the gym.

Introduce database migrations and test upgrading a database that already contains workout data.

**Deliverable:** an app that remains useful after several weeks of real records.

**Weeks 7–8: Automate infrastructure and releases**

Bring your cloud resources under Terraform. Automate deployment after checks pass, manage secrets outside the repository, and document how to roll back a release.

**Deliverable:** you can explain and reproduce the path from a code change to a running application.

**Weeks 9–10: Practise operating it**

Add useful logs, request-error metrics, and an alert. Configure database backups and restore one into a separate database.

Deliberately introduce a failed deployment or unavailable database, then use your monitoring to diagnose it and recover.

**Deliverable:** evidence of a successful rollback, backup restoration, and investigated failure.

**Weeks 11–12: Buffer and portfolio polish**

Finish incomplete work, improve accessibility, and write a README covering architecture, local setup, deployment, costs, and tradeoffs. Record a short demonstration.

Only add another feature if the core application is stable.

**Use a feature-driven learning rule throughout:** pick the next deliverable, learn what is needed to complete it, implement it, and write a few notes about what you learned. This makes “learn databases” become “store my workouts correctly” and “learn DevOps” become “deploy my next change safely.”