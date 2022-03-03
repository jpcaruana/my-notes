# An elegant puzzle, Systems of Engineering Management
by Will Larson

# 1. Introduction
Author has an experience of rapid growth (200 to 2000 engineers) at Ubr, then Stripe.

# 2. Organizations
Organization = collection of people working towards a shared goal.

## 2.1 Sizing teams
His framework:
- managers should support 6 to 8 engineers
	- < 4: you are a Tech Lead Manager
		- mix of management and technical leading
		- limited carrer oppotunities
		- will spend less time on technical details
	- > 8: you are a Coach
		- too busy to invest in their team
		- just a safety net for problems
- managers of managers should support 4 to 6 managers
- on-call rotations want 8 engineers
	- two tier 24/7 = 8 engineers
- small teams (<4 members) are not teams
	- a group of individuals
- keep innovation and maintenance together
	- do not make an innovation team out of maintenance teams: it creates a 2-tiered class system
	- innovate within existing teams, you'll get better results and higher morale, a culture of learning

The scale playbook is simple :
- teams should be 6 to 8 during steady state
- to create a new team
	- grow an existing team to 8 or 10
	- then cut into 2 teams of 4 to 5
- never create empty teams
- never leave managers supporting more than 8 engineers

## 2.2 Staying on the path to high-performance teams
Team reorg is painful but resolves quickly. It is much harder to keeping the faith when you played your cards and need space for your plan to come to fruition. Stay, so you learn.

Hiring is not the only way.

The 4 states of a team, from "falling behind" to "innovating":
1. falling behind: hire
	- how
		- backlog grows
		- people work hard, little progress, low morale
	- solution: hire (outside of the company)
		- celebrate easy wins
		- inject optimism
2. treading water: reduce WIP
	- how
		- get their critical work done
		- but not paying their technical debt
		- morale is a little higher, people are still working hard
	- solution: reduce WIP
		- help people transition from personal view of productivity to a team view
3. repaying debt: add time
	- prevent the impacience from users for features
4. innovating: add slack

Theses (systemic) fixes are slow, but they last long.

Don't try to fix all the teams in one state at once, focus on one team for one state. For instance, hire for one team. It is easier to hire several people at once in a team (a little disruptive, but more efficient in the long run) -- true for "repaying debt" but not for "innovating" teams.

## 2.3 A case against top-down global optimization
Why you shouldn't move people from a team that is repaying debt to others? 
- Team first
	- sustained productivity comes from high-performing teams. Disassembling a team leads to significant loss of productivity for both teams
	- team culture requires time
- Teams have High fixed costs and relatively small variable costs
	- moving one person can shift a team from "innovating" back to "falling behind"
- Great teams employ slack very well (in incremental and novel ways) with minimal coordination costs

It is more usefull to move _scope_ between teams, preserving the teams themselves. If a team has a lot of slack, you can (slowly) move more responsability to them. It preserves system behaviour. It can also be usefull to rotate individuals for a short period of time  into an area than needs help ; they retain their identity/membership to their team and are not splitting focus between work and finding membership.

## 2.4 Productivity in the age of hypergrowth
Doubling head count every 6 month is a new company. Corrolary: our processes are always 6 months behind.
- more enginneers, more problems
	- nb trainees > nb trained employees (it takes time to onboard an engineer to be fully productive)
	- take time spend on hiring into account too
	- but also:
		1. every additional order of magnitude of engineers -> design/maintain a new layer of management
		2. for every 10 new engineers -> additional team -> more coordination
		3. each engineer -> more commit/day -> more deploy/day -> more load of development tools
		4. more deploy -> more outages-> more incident management, mitigation, post mortems
			- (that's not what I see at Deepki)
		5. prod: more engineers -> more specialized teams/systems -> more on-call rotation
			- (think DRIS here ?)
- more employees, more customers, more problems

# 3. Tools
# 4. Approaches
# 5. Culture
# 6. Carreers
