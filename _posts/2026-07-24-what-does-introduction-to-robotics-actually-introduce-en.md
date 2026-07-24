---
layout: post
title: "What Does Introduction to Robotics Actually Introduce?"
date: 2026-07-24
lang: en
---

*[阅读中文版](/2026/07/24/what-does-introduction-to-robotics-actually-introduce-zh/)*

Tianyang Shen

The first time I realized something was wrong, I was staring at a point cloud.

I had just finished Introduction to Robotics that semester. My grade was fine, and I felt I had finally gotten through the door. Wanting to try my hand at something real, I gave myself a job: a camera looks at an object on a table, and a robot arm goes over and picks it up. The arm half didn't worry me at all. Forward and inverse kinematics, Jacobians, trajectory generation: I had derived all of it in homework more times than I could count.

Then I got stuck on step one. That cluster of points on the screen: I had no idea how an object's pose was supposed to grow out of it.

It wasn't that I couldn't write the code. It was that I didn't know whose problem this was, where one would start learning it, or even that it had a name.

There would be more places like that ahead. I didn't know what a trained policy has to go through before it lands on a real robot. I didn't know how perception, planning, control, and learning mesh into a system that actually moves. Above all, I didn't know that robot learning was a continent unto itself, with its own methods, courses, and an entire community, and until then I hadn't even known there was land on the other side of the sea.

I wasn't standing at the entrance to a field. I was standing in fog. Worse, no one had ever told me which way to walk once it lifted.

## What the course gave me, and what it didn't

The course was the introduction I took in my third year in an EE department, and it marched chapter by chapter through Lynch and Park's *Modern Robotics*: configuration space, rigid body motions, forward and inverse kinematics, dynamics, trajectory generation. The homework was solid. We wrote numerical IK solvers in MATLAB, built URDFs, ran them in Gazebo. The professor worked on legged robots, and when the mood struck him he gave us a lecture on the whole-body kinematics of his quadruped.

By the end of the semester I could take a 6-DOF arm from rotation matrices all the way to Newton-Euler without skipping a step. And that point cloud? I couldn't even say which part of the field was supposed to deal with it.

At the time I assumed the gap between those two facts was simply material I hadn't gotten to yet. So I kept walking: picking a direction, reading papers, preparing a first project. The deeper I went, the fewer paths there were under my feet. I tried to reproduce a manipulation policy and discovered I didn't understand how it perceived objects. I tried to build an imitation learning pipeline and discovered that learning, the entire block of it, was blank in my head. Every paper demanded prerequisites nobody had ever taught me. What I was missing wasn't a knowledge point here or there. It was whole slabs of foundation.

Only later did I understand what that course had actually given me: a surveyor's map, one that charted a single province, "how a robot arm moves," down to the centimeter. What it hadn't given me was the map that shows all the provinces.

## So I went through the courses one by one

Carrying that question, I went and read the intro courses at a few schools with robotics in their course catalogs.

The first thing I saw was a clean split, and Stanford is the tidiest specimen because it offers both kinds. CS223A is Khatib's course on the modeling, planning, and control of robotic systems, essentially a grand tour of geometry, kinematics, statics, dynamics, and control. It is the kind I took. [CS237A](https://bulletin.stanford.edu/courses/2185453), Principles of Robot Autonomy I, is about equipping a mobile robot with perception, localization and SLAM, nonlinear and learning-based control, motion planning, and decision-making under uncertainty. One grew out of the mechanical and electrical engineering tradition and teaches the mathematics of arms; the other grew out of the computer science tradition and teaches the autonomy of mobile robots. Both are taught seriously, both have real hardware and plenty of code, and both are good courses.

If the story ended here, the conclusion would be elegant: there is no single unified Introduction to Robotics, only two, and which half of robotics you learn depends on which department's door you pushed open in your junior year.

Unfortunately, that conclusion is wrong. CMU's 16-311 ([since renumbered 16-281](https://coursecatalog.web.cmu.edu/schools-colleges/schoolofcomputerscience/robotics/robotics.pdf)) lists vision, machine learning, motion planning, mobile mechanisms, forward and inverse kinematics, and sensors all in one course description; it covers mobile robots and arms alike. [Berkeley's EECS C106A](https://undergraduate.catalog.berkeley.edu/courses/1547841) is even more complete: the full arm curriculum with nothing missing, plus geometric motion planning and obstacle avoidance, low level vision, and structure from motion, and near the end of the term a lab literally titled Fullstack Robotics: Perception, Planning, and Control, in which students use MoveIt to compute IK and wire perception and planning together to drive a UR7e arm.

The dichotomy doesn't hold. Broad courses exist.

But laying these syllabi side by side, I realized I had been asking the wrong question from the start. I had been counting whether learning gets mentioned. It does, and in more than one place.

Stanford CS237A's official description includes learning-based control, wedged between nonlinear control and motion planning, occupying the width of one comma. Berkeley C106A has "an introduction to vision & learning," hanging off the end of structure from motion. CMU's [2019 syllabus](https://www.cs.cmu.edu/afs/cs.cmu.edu/academic/class/16311/www/s19/syllabus/syllabus.html) (the most detailed one I could find from before the renumbering; the post-renumbering description lists the same content, and the shape looks unchanged) gives the most: week four has a full session on Reinforcement Learning, followed immediately by a guest lecture from Oliver Kroemer titled, precisely, Learning for Manipulation, given by someone who does manipulation learning for a living.

So the name was given. The name was given, and I was still standing in fog.

The real difference isn't whether learning gets mentioned. It's what a course takes as its through-line, and what it uses to explain failure. All of these courses have models as the through-line: model it, solve it, implement it. Learning appears as an item in a catalog, not a link in the chain. And the deadlier half is the authority over failure: when a method in the course doesn't work, the reason given is always that the model isn't good enough yet, the parameters aren't calibrated yet, the constraints aren't all written down yet. It is never "this class of problem was never meant to be solved by solving equations."

What learning needs has never been that line in the catalog. It needs the role of explaining where the boundary lies. And that role, the first course has never given it.

The follow-up courses at the two schools offer two different sequels. Stanford's [CS237B](https://web.stanford.edu/class/cs237b/pdfs/syllabus.pdf), Principles of Robot Autonomy II, covers the relationship between reinforcement learning and optimal control, contact and dynamics models for prehensile and nonprehensile manipulation, and imitation learning with human intent inference. There, learning finally becomes the through-line. But it is a sequel: it requires CS237A, and a student standing inside the first door cannot see the second one. Berkeley's C106B teaches the kinematics and control of dexterous hands, grasping and manipulation, nonholonomic motion planning, SLAM, and active vision; the core content is uniformly classical. Reinforcement learning does appear, exactly once, in the slot for additional research topics at the instructor's discretion, alongside drones, soft robots, and AR/VR.

The hardest case to explain is CMU. It didn't push learning off to a sequel. It put it in week four of the first course and invited someone from the field to speak. By all rights, that course should have been able to deliver students to the continent.

I puzzled over this for a long time without an answer. I'll come back to it.

## An objection I have to answer first

Before going further I have to stop, because there is a strong objection: syllabi are public. What the course teaches is printed in black and white right under its name, and I chose it. Nobody deceived me; I just had no one to point the way. This is a problem of course selection and advising, not of course design.

The objection is partly right, and I concede that. If a senior student had told me at registration, "this course only covers arms; if you want to work on manipulation policies you'll need to go watch CS285 on your own," I would have saved a great deal of effort over the following two years.

But it rests on a fatal premise: it assumes I knew what to look up. A person who doesn't know robot learning exists will not search for robot learning. Unknown unknowns have no search entry point. You cannot go look up a thing you don't know has a name. This is the most fundamental wall in self-study, and it is why "go look it up yourself" is nearly useless advice for a beginner.

And the objection makes the problem bigger, not smaller. Because it amounts to conceding that someone has to hand you this map, just not necessarily that course. And the reality, at least across the courses I surveyed and the one I took, is that no link in the undergraduate pipeline is responsible for handing it over. Curriculum committees make sure each course meets its content bar. Advising handles credits and graduation requirements. Each professor makes sure their own course is taught well. "What this field looks like as a whole, and where you currently stand in it" falls into the gap between everyone's job descriptions.

Which makes putting it into the first course the cheapest fix, because that course is the one place everyone passes through, at the precise moment when they still know nothing.

## Then why does no one point it out in the first course?

The first layer of the answer hides inside the phrase "grew out of a department."

Robotics was born out of other disciplines. In mechanical and electrical engineering, the original problem was making industrial arms move precisely, and out of it grew the kinematics, dynamics, and control branch. In computer science, the original problem was making a moving machine find its own way, and out of it grew the perception, planning, and estimation branch. The professors who define these intro courses were trained inside their respective traditions, and the maps they draw are naturally the half they know best. This isn't favoritism. Each person can only hand over what is in their hands.

But history alone doesn't explain it, because inertia can be broken, and after several decades it hasn't been. There is a deeper layer, and it is the shape of the mathematics itself.

The arm branch is easy to teach well because its content naturally forms a chain: rotation matrices lead to twists, twists lead to the Jacobian, and the Jacobian leads on to dynamics and control. Link locks into link, one semester walks it end to end, and every step yields a homework problem with a standard answer. The rest, perception, planning, learning, has no such iron prerequisite structure between its parts: point cloud registration doesn't require motion planning first, and behavior cloning doesn't require SLAM. They are loose puzzle pieces that will not assemble into a through-line you can teach in one breath.

And so the branch that is easiest to teach well became, year after year, the whole.

## A chain teaches you two things

But the skew in content is not the deepest effect. Beyond content, a derivation chain teaches something deeper: what counts as an answer.

I know this because I watched it happen in myself. Spend a semester inside that chain, where every problem has a closed-form solution, and every "I don't know" eventually resolves into "I haven't derived it yet." When I later read learning-based manipulation work for the first time, my first reaction was not "here is a new continent." It was "that doesn't count as solving it."

So it wasn't that I didn't know it existed. It was that I didn't think it counted. Of these two kinds of absence, the second is far harder to detect in yourself, because it doesn't present as a blank. It presents as disdain.

I don't know whether this happens to other people. But if it does, it is much worse than a coverage problem. A gap in coverage can be filled by catching up. "What counts as an answer" is the very ruler you use to decide what is worth catching up on. If the ruler is bent, the motivation to fill anything never forms.

And this finally explains why CMU's two sessions didn't take. The trunk of that course is classical methods; the project is a LEGO robot driven by a microcontroller; the shape of the whole course is build it, compute it, tune it. Inside a container like that, one Reinforcement Learning lecture doesn't register as a door. It registers as a digression. And Kroemer's session was, in name and form, a guest lecture. The word itself means someone from outside.

What was missing was never podium time. It was the shape of the course the lecture sat inside.

## And the chain is closed

There is one more layer, and I think it is the most damaging one.

A course can tell you it has gaps in two ways. The first is explicit: the syllabus says this course does not cover X. That kind of gap heals itself. The second is implied by shape, and shape lies.

The arm chain starts at rotation matrices and ends at torque commands. The causal chain is complete; not one interface is left dangling. Walk it to the end and you come away with a very real feeling that the subject has been fully told.

That is exactly what makes it dangerous. **The more complete a course is, the more it looks like everything.**

My guess is that the looser mobile robot course actually leaks less, precisely because it never offers that feeling of completeness: students walk out knowing they are holding a bag of parts. That half is conjecture; I never took that course. But the other half is not: I walked out believing I was holding a machine.

## "Hard" is not "impossible"

Everything above explains why things are this way. It does not prove they have to be.

I considered CS231n as a counterexample and found that it fails. Deep learning looks sprawling, but from start to finish it has exactly one mathematical object: a differentiable parameterized function trained by gradient descent. That is a chain even tighter than the arm's. What it proves is that anything with a chain can be taught well, which lands squarely on the same side as the previous section's argument.

Follow that thought and you arrive at a plan that looks workable: fine, then let robot learning have its own tightly chained course. That course already exists. CS285 is one; MIT's manipulation course is another. But they don't solve this essay's problem: a student who doesn't know the continent exists will not enroll in the course about it. However good a standalone course is, it is visible only to people who already hold the map.

The real counterexample has to come from a field that natively refuses to form a chain, and the computer systems course is one. From binary representation, to C and assembly, to processor architecture, to caches and the memory hierarchy, to linking, exceptional control flow, virtual memory, and concurrency. There is no mathematical derivation connecting these layers; you cannot derive virtual memory from two's complement. What arranges them into one course is something else: a single question that every piece of content must answer. When you write a line of code and press run, what happens between here and the silicon? Each block is placed by its distance from that question, and the ordering falls out on its own.

So order doesn't have to grow out of mathematics. It can grow out of a question. And what the robotics intro course lacks is exactly that question.

The arm course secretly answers "how does an arm move." The mobile robot course secretly answers "how does a vehicle get there." Both questions are too small: small enough to close the moment they are answered.

The question that is big enough has been sitting there all along; no one has treated it as the organizing principle of a course. For a machine to get something done in the physical world, what has to happen in between? It naturally calls perception, planning, control, and learning onto the stage in turn, because remove any one of them and the thing doesn't get done. And it naturally admits a boundary, because push the answer far enough and you inevitably hit "nobody knows how to do this part yet."

Maps don't grow on their own. But what's missing isn't a person willing to draw one. It's a question worth drawing one around.

## What an Introduction to Robotics should introduce

My answer: it should be a roadmap.

First, what a roadmap is not. It is not cramming perception, planning, control, and learning each into one semester at full depth. That is unrealistic and unnecessary. Force-feed diffusion policy to a third-year student with no prerequisites and all you get is a pile of library calls that won't converge. A map's job has never been to walk you across every inch of ground. It is to let you know where each territory is, what it looks like, how the territories border one another, and which direction to head when you want to go deep.

Concretely, a competent intro course should leave students able to answer three questions on the way out:

**What regions are on this continent.** What problem perception, planning, control, and learning each solve, and what each one's core difficulty is.

**How they assemble into a robot that moves.** An object is seen, decided upon, and picked up: how data and commands flow between these blocks, where the interfaces are, and where the errors accumulate.

**Where the road is if you want to go deep in one of them.** Which grad course, which book, which line of papers.

## How learning should enter the course

By the standard above, the answer looks simple: give it one survey lecture, make clear that the continent exists, and be done.

That is what I used to think, until I looked at CMU. It gave more than one session, brought in a practitioner, and the result was still what it was. So giving the name is not enough, and giving the slot is not enough. As long as the shape of the container doesn't change, whatever you insert gets read as an interlude.

What actually works is not introducing a method. It is staging a failure.

Give students a task their current tools just barely cannot reach. Grasp a piece of cloth. Push a box to a target across a table with unknown friction. Pull the middle object out of a cluttered pile. Have them actually write the equations, actually build the controller, and actually fail. And make sure the failure lives in the model itself: contact parameters that cannot be measured, state that is only partially observable, several equally reasonable actions from the same state.

At that moment, saying "there is a continent devoted to exactly this kind of problem; it is called robot learning; its move is to not solve this equation, and to learn the policy from data instead; and the hottest thing on that continent right now is called the robot foundation model, which trains one policy on large-scale multi-task data to generalize across robots and tasks, instead of hand-writing a pipeline per task" lands in an entirely different way. It is no longer a new noun. It is the answer to a problem the student just crashed into with their own hands.

This also repairs the ruler from earlier. What students carry out is no longer "robot problems can be solved," but a more accurate version: some robot problems can be solved and some cannot, and learning to tell the two apart matters more than knowing how to solve the first kind.

One lecture's worth of time, zero prerequisite load, not on the exam. That is all, and it is exactly what I lacked most. I was never afraid it would be hard. I was afraid of not knowing it existed.

## If I were to redesign the first course

**Whole picture first, depth second.** Don't rush into derivations in the opening weeks. First fly students over the entire continent: a real robot going from seeing to acting, and how commands flow between the blocks. Even if each block gets only two weeks. Even if the theory is only skimmed. What a newcomer needs first is a coordinate frame, and only then the details at one coordinate. Spending an entire semester deriving every property of the Jacobian serves them far less than first knowing where the Jacobian sits on the map.

**Show them more than one kind of robot.** At minimum, let students see the two most basic bodies, wheels and arms, and learn that navigation and manipulation are two different ways of being a robot, with difficulties that differ at the root. You could even let students choose a track by interest at the start: the wheels track does perception, planning, and navigation; the arms track does perception, grasping, and control. The first half shares one base map; the second half goes deep separately. One course with two exits, patching exactly the crack left by two departments each teaching half.

**Tell them where the boundary is, and what the boundary means.** An intro course need not, and cannot, teach the frontier. But it can annotate the edges of the map: this way lies robot learning, that way lies whole-body control, and over here is a fast-growing new landmass called the foundation model. More important is making students understand that the boundary is not "what the instructor didn't get to." It is "what the field itself doesn't yet know how to do." Those are entirely different things inside a student's head. The first makes you feel ignorant. The second tells you there is something you could go work on.

## I know what this costs

Leaving those three points as stated would be irresponsible. Anyone who has actually taught this course will immediately raise three questions, and I will try to answer them head-on.

**Who teaches it?** This is the hardest one, and the difficulty is ironic: a course spanning four blocks needs an instructor fluent in all four, and such people are the scarcest, for exactly the first-layer reason above. The professors who define intro courses are themselves products of the split. Expecting any one of them to draw the whole map alone means asking them to teach what they don't know. So the course shouldn't be taught by one person in the first place. It is closer to a seminar in its organization: a lead instructor owns the through-line and the connective tissue, and each block gets two weeks from someone working in that area. The cost is coordination, plus one person who genuinely designs the through-line rather than stapling four slide decks together.

**What about the homework?** Roadmap courses all die here. Lectures can be broad; homework cannot. Broad homework degenerates into book reports.

The only way out is a single spine assignment running the whole semester: a minimal grasping pipeline, built end to end, with each block done at its thinnest viable layer. Perception isn't 6D pose estimation; it's one camera calibration plus color-blob segmentation on a plane. Planning isn't sampling-based planning; it's one joint-space interpolation under an obstacle constraint. Control uses an off-the-shelf position controller, but students must explain why it breaks down the moment contact begins. Learning trains nothing: students receive a pretrained policy and wire it into the pipeline.

In fairness, someone has already built ninety percent of this. Berkeley's Fullstack Robotics lab, with perception, planning, and control chained onto a real machine, is exactly this shape. It is missing only two things: the learning block never enters, and the final question never gets asked. And I would argue that what the whole course truly exists to teach lives precisely in that question: **under what conditions does it fail, and why.** That question should run the length of the semester, answered anew with every block handed in.

**And the cost of the split tracks?** Two TA staffs, two sets of hardware, two sets of assignments, and two sets of late-night debugging. That is real money and real people. A resource-tight department can step back one notch: share all the lectures and split only at the final project, half the class on a mobile platform and half on an arm, with demos for each other at the end. Shared overview, forked depth, at the cost of supporting one extra project.

## Back to the original question

Introduction to Robotics: what did it actually introduce?

I don't regret taking that course. The surveyor's map it gave me is the real thing. I still use it today to work out an arm's motion with complete clarity, a foundation no learned policy can substitute for. But if someone asks me, "after this course, have I been introduced to robotics?", my honest answer is: you have been introduced to one province, how a robot arm moves. Robotics is a continent.

I am still walking that continent myself. I am writing this not because I have crossed it, but because I still remember the panic of standing in the fog, not knowing which way to step.

But saying "your map is incomplete" and stopping there is cheap. An essay that spends its whole length complaining that nobody draws the map, and then draws none, has no standing to complain. So at the end of this essay I have listed what I spent the past two years filling in. Only after finishing the list did I notice something a little funny: **this catch-up list is the photographic negative of the missing map.** Every item on it is something someone should have pointed out to me at the start, and that I instead discovered by crashing into it.

It is certainly incomplete, and certainly biased toward my own direction. I work on manipulation, so that region is drawn in finer detail than the rest. But at least it is an actual map, and not one more sentence about how much maps matter.

The deepest bind for a beginner has never been that some particular thing is hard. It is that they do not know the thing exists, and therefore cannot know they should learn it.

What a map really saves is not the effort of walking. It is the detours you didn't even know you were taking.

If you have just pushed open some door, I hope you won't have to find out what lies behind each wall the way I did, one collision at a time.

---

## Appendix: a starter map for the manipulation direction

Each block follows the same format: what it solves, why you'll need it, where to start.

### 0. What you may already have: rigid body motion, arm control, and motion planning

**What it solves:** Given the joint angles, where is the end-effector; to put the end-effector somewhere, how should the joints move; how much torque does the motion take; and how to find a collision-free path through configuration space.

**Where to start:** Lynch & Park, *Modern Robotics*, with a free PDF and companion videos online. If you took that course, you already have this block, and chapter 10 gives a serviceable overview of motion planning; to go deeper, the configuration space and sampling-based planning chapters of LaValle's *Planning Algorithms* (free online) are enough.

**Next step:** Russ Tedrake's Underactuated Robotics notes (MIT 6.8210, formerly 6.832, all free online). They tell you what to do when a robot cannot simply be "computed," and they are the best bridge from classical control to modern methods.

### 1. Vision and deep learning: the foundation of modern perception

**What it solves:** Getting "what is in the scene, where it is, and in what pose" out of images and point clouds.

**Why you'll need it:** Every real grasp starts here. This is the first step I got stuck on.

**Where to start:** Szeliski, *Computer Vision: Algorithms and Applications* (free online) for the geometry and multi-view foundations. For the deep learning half, CS231n.

### 2. State estimation and SLAM: letting the robot know where it is

**What it solves:** Sensors are noisy and models are wrong; how do you estimate a reliable state from a stream of unreliable observations.

**Why you'll need it:** Even if you only work on arms, the filtering and factor-graph way of thinking keeps reappearing in calibration, force estimation, and contact-state inference.

**Where to start:** Thrun, Burgard & Fox, *Probabilistic Robotics*. An old book, but the basic language of the probabilistic branch is all in there.

### 3. Reinforcement learning and imitation learning: the trunk of learning-based control

**What it solves:** When a policy is too hard to write by hand, how to learn it from interaction or from demonstrations.

**Why you'll need it:** Nearly all frontier manipulation work now stands on this block. This was my most complete blank.

**Where to start:** Sutton & Barto, *Reinforcement Learning: An Introduction* (free online) for the concepts, then Berkeley CS285 (Sergey Levine; public lectures and assignments) for the modern half. Imitation learning has no standard textbook; the fastest route is the original papers along the behavior cloning and DAgger line.

### 4. Generative models as policies: the core of today's manipulation policies

**What it solves:** In demonstration data, the same state often maps to several reasonable actions, and direct regression averages them into one unreasonable action. Generative models exist to handle exactly this multimodality.

**Why you'll need it:** This block barely exists in classrooms. You dig it out of papers and tutorials, and it happens to be where the field is most alive right now.

**Where to start:** The Diffusion Policy paper (Chi et al.) is the best entrance; afterwards, circle back for the basics of diffusion models and flow matching.

### 5. Grasping and force control: landing all of the above on one contact

**What it solves:** Where to grasp, how to grasp, why position control breaks once contact begins, and how force should be controlled.

**Why you'll need it:** You can get everything above right and still fail to pick the thing up on real hardware. Physical contact is where the entire sim-to-real gap comes due at once.

**Where to start:** Tedrake's [MIT Robotic Manipulation](https://manipulation.mit.edu) (undergrad 6.4210, grad 6.4212; notes and assignments all free online). It is the only course I have seen that truly chains perception, planning, and control into one manipulation pipeline, with model-based and learning-based methods standing side by side rather than sitting in an appendix. In a sense, it is the advanced edition of the map in this essay.

### 6. Past the boundary: the parts still growing

**Robot foundation models:** Train one general policy on large-scale, multi-robot, multi-task data, aiming at generalization across embodiments and tasks. Read along the line from the RT series to Open X-Embodiment, and you can watch the idea being pushed forward step by step.

**World models:** Let the robot rehearse in its head before acting: learn a model of "given the current state and an action, what does the world become," then evaluate, improve, or even directly generate policies inside that imagination. The term hasn't converged yet. The same name covers latent dynamics, action-conditioned video generation, and 3D scene prediction, and that confusion is itself evidence that the area is still on the boundary. For the concept's origin, start from the Dreamer line of model-based RL, then look at how video generation models are being wired into manipulation. This line and the foundation model line above are merging.

No reading list for this block, just the two lines above, because it changes its face every few months. A fixed list is useless here. What you want to build is the habit of following: pick a few groups, and track their pages and arXiv.
