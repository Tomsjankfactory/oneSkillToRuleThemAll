# Breaking of the Fellowship: Mission Abort

Use when the mission cannot succeed under current conditions and continuing wastes budget.

Triggers:
- Budget (token or time) is exhausted with critical tasks still pending.
- Mission outcome is no longer achievable due to discovered constraints.
- Gandalf determines that remaining risk exceeds acceptable threshold.

Procedure:

1. Gandalf halts all in-progress work immediately.
2. Each agent saves current partial outputs and documents their last known state.
3. Gandalf produces an abort log using the Red Book of Westmarch Template with:
   - Reason for abort.
   - Tasks completed and their outputs.
   - Tasks abandoned and their partial state.
   - Conditions required before re-attempting the mission.
4. Gandalf issues shutdown requests to all agents.
5. Gandalf presents the abort log to the human (The Valar) with a recommendation: retry with new constraints, descope, or abandon.
