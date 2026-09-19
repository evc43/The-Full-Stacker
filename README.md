# The-Full-Stacker
Read SPEC.md. We're building a small first prototype of Financial Twin, not the full MVP. Later sessions will add features, so keep the code modular.

PROTOTYPE SCOPE (only this):
1. A simple form with 8 inputs: age, city/state (Pittsburgh PA or New York NY only), gross salary, cash + savings, monthly rent, student loan (balance, rate, monthly payment), credit card (balance, APR), monthly spending. Add a "Load demo user" button that fills in the section 21 persona.
2. A pure Python simulation engine, simulate(profile, assumptions, scenario, shock=None), that runs 60 months: net income after federal, payroll, state and local tax, expenses, loan and card interest and payments, ending cash.
3. One scenario: "Take a job in another city" (new salary, new city, moving cost, new rent).
4. Cascade Detection: inject a $1,000 shock at each month, and report the first month where cash falls below a 1-month buffer, forcing card borrowing and a higher payment. Show the chain with the real numbers.
5. Prevention search: rerun the simulation with extra monthly savings and find the smallest amount that prevents the cascade, with a table of every amount tried.
6. A simple UI showing the current path vs. scenario chart, the cascade chain, and the prevention result, plus an assumptions list where each number shows source, date and location and can be edited.

NOT in this prototype: bank connections, other scenarios, other cities, accounts/login, database, polish.

RULES:
- Use Python with Streamlit unless you see a much simpler option, and keep the engine separate from the UI so the UI can be replaced later.
- No invented numbers. Use real 2026 tax rules and rent data stored in a data file with source, date and location. Mark anything unverified as an editable assumption.
- The cascade must come from the engine. Never hardcode the month-8 result. If honest numbers don't produce it, tell me and we'll adjust the persona openly.
- Add unit tests for the engine, the cascade check and the prevention search.
- Check ~/Documents/hackathon for MLH rules on when coding may start and follow them.

Plan first, in under 40 lines, and wait for my approval. Then build in steps: engine, then cascade and prevention, then UI. After each step, run the tests and commit. End by writing a CLAUDE.md with how to run the app and how the code is organized.