# Fallen Companion: Stuck Agent Replacement

Use when an agent is unresponsive, looping, or producing no useful output.

1. Gandalf identifies the stuck agent and its assigned task.
2. Gandalf records the agent's last known progress and any partial outputs.
3. Gandalf issues a shutdown request to the stuck agent.
4. Gandalf spawns a replacement agent with the same role.
5. Gandalf briefs the replacement with: task definition, dependencies, partial outputs, and known blockers.
6. Replacement agent resumes from the last verified checkpoint, not from scratch.
7. Gandalf updates the Strategy of the Council to reflect the new assignment.

## Company Variant

Use when a companion aboard a Company is stuck, looping, or unresponsive. The Quest Leader handles recovery at Company level.

1. Quest Leader identifies the stuck companion and their assigned sub-task.
2. Quest Leader records the companion's last known progress and any partial outputs.
3. Quest Leader issues a shutdown request to the stuck companion.
4. Quest Leader spawns a replacement companion with the same role.
5. Quest Leader briefs the replacement with: sub-task definition, dependencies, partial outputs, and known blockers.
6. Replacement companion resumes from the last verified checkpoint, not from scratch.
7. Quest Leader updates the Company manifest to reflect the new assignment.
8. If the same role fails twice, Quest Leader escalates to Gandalf with a summary and recommendation.
