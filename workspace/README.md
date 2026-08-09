# Career Workspace

This directory is intentionally empty in a fresh clone. Create one workspace per candidate or keep a private workspace outside the repository when it contains personal data.

Suggested layout:

    workspace/
      candidate-profile.json
      enhancement-claims.json
      jobs/
      applications/
        <job-id>/deep-dive/
      weak-points.json

Validate new records against the contracts in `../schemas/` before handing them to another Skill.

Use `applications/<job-id>/` to store the JD snapshot, tailored Resume Model, submitted DOCX, and one file per interview round. Keep a real workspace private; repository fixtures contain only synthetic data.

For an independent project deep dive, use `deep-dive/YYYY-MM-DD-<topic>.md` at the workspace root. For an application-specific deep dive, keep the note under `applications/<job-id>/deep-dive/` so interview preparation can read the same project context as the submitted artifacts.
