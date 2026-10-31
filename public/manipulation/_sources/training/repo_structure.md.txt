# Repository Structure

This repository is intended for downstream Isaac Lab training formulations.

Shared infrastructure lives under `src/isaaclab_training/`:

- `mdp/`: reusable MDP terms and deploy-aware action wrappers.
- `export/`: LEAPP export helpers used by the generic exporter.
- `cli/`: package console commands.
- `utils/`: small runtime helpers shared by tasks and CLIs.

Concrete task formulations live under `src/isaaclab_training/tasks/`.

To add a task:

1. Create `tasks/<task_name>/`.
2. Put task-specific scene assets, offsets, rewards, and config classes there.
3. Reuse shared terms from `isaaclab_training.mdp` where possible.
4. Register Gym task IDs in the task config package.
5. Add focused tests for task registration and deployment metadata.

Use `IsaacTraining-...` task IDs for new tasks. Keep legacy aliases only when moving an existing task from another package.
