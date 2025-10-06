# Genetic Algorithm Assignment
30% of the overall grade for this module

Marks indciated in sections below are based on percentage of marks allocated for this module

In this assignment you must choose a problem, and attempt to use the Genetic Alogrithm that we developed in class to solve this problem.



## The Problem
---

The task is to design a timetable for a college course, where subjects, classrooms, and lecturers are assigned to timeslots, ensuring there are no conflicts with the room schedule, teacher schedule, or subject schedule. The goal is to maximize the efficiency and accuracy of the scheduling process, adhering to the constraints such as:

* No Room Conflicts: A classroom can only be assigned to one subject at any given time.
* No Lecturer Conflicts: A lecturer can only teach one subject at a time.
* No Subject Conflicts: A subject should be assigned to only one timeslot for each day.
* Breaks times being an hour break from 1 to 2
* Half days on friday to fit with the colleges schedule.


These constraints are important because they ensure that the schedule works without clashes, allowing efficient use of resources (rooms and lecturers) and providing students with a smooth educational experience.

---
Rough work done through og this whole assignement can be fund in this notebook: [Conor Dawson Genetic Timetable Roughwork](https://colab.research.google.com/drive/1y4T_XFOJQrDGXN7Z9RxvTJntL_F9PKV4#scrollTo=xQVqWRm523qK)


---

1. **Handling Complex Constraints**

  A genetic algorithm (GA) efficiently handles multiple timetable constraints:

  * *Room Conflicts:* Ensures no two subjects are scheduled in the same room at the same time.

  * *Lecturer Conflicts:* Guarantees lecturers are not double-booked.

  * *Subject Conflicts:* Ensures subjects don’t overlap in the same timeslot.

  * The GA evaluates timetables based on a fitness function that penalizes timetables with conflicts, guiding it to conflict-free solutions.

---

2. **Resource Utilization with Minimal Conflicts**
  The GA maximizes resource efficiency, ensuring:

  * *No double-booking:* Resources (rooms, lecturers) aren’t assigned multiple tasks at the same time.

  * *Optimal scheduling:* Resources are allocated in the most efficient way possible.

  * The fitness function prioritizes timetables that make optimal use of available resources.

---

3. **Crossover to Ensure Diverse Solutions**

  Crossover creates new timetables by mixing parts of parent timetables. It ensures:

  * *No duplication:* Partially Mapped Crossover (PMX) prevents duplicate class assignments.

  * *Valid replacements:* Crossover respects subject, room, and lecturer assignments, preserving timetable integrity.

  * Crossover generates new, diverse timetables that combine the best aspects of parents.

---

4. **Mutation for Exploration and Avoiding Local Optima**

  Mutation introduces random changes to explore new solutions, preventing the algorithm from settling on suboptimal results.
  
  *It:*

  * *Introduces new combinations:* A random change might lead to a better solution.

  * *Maintains diversity:* Mutation prevents early convergence, helping find * optimal solutions.

  * This keeps the GA from getting stuck in local optima, ensuring continuous improvement.

---

5. **Iterative Improvement**

  The GA improves timetables over generations:

  * *Selection:* Timetables with fewer conflicts are selected for reproduction.

  * *Offspring generation:* New timetables are created by crossover and mutation.

  * *Steady improvement:* The population evolves, resulting in increasingly efficient timetables.

  Each generation refines the solution, leading to better results.

---

6. **Scalability**

  The GA easily scales to handle large timetables with many subjects, rooms, lecturers, and timeslots. Its population-based approach works efficiently even as the problem size grows, continuously searching for optimal solutions.

---

# The problem and the cost function   


---



# ***Imports Used***

* ***random:*** Used for random selection, mutation, and crossover operations.

* ***prettytable:*** Used for formatting the output timetable in a structured table.


---


# **Define Problem Parameters**

Defines the courses, subjects, teachers, classrooms, days, and available time slots.

 **Also defines genetic algorithm parameters:**
* ***POPULATION_SIZE:*** Number of timetables per generation.
* ***GENERATIONS:*** Number of iterations to evolve the best timetable.
* ***MUTATION_RATE:*** Probability of random mutation in a timetabl



---



# **Generate a Random Timetable (Initial Population)**

* This function generates a random timetable for a given course.
* It ensures that each subject appears twice per week.
* It randomly assigns days, time slots, teachers, and classrooms.
* This function initializes a population of chromosomes (timetables).

***Genetic Terms:***

* Gene: A specific time slot entry containing subject, teacher, and room.
* Chromosome: A full timetable, consisting of multiple genes.

---

# **Define the Fitness/Cost Function**

* The fitness function evaluates the timetable.
* It penalizes scheduling conflicts:

  * Same teacher in multiple slots (-100 points).
  * Same room occupied by multiple subjects (-100 points).
  * Same subject appearing more than twice in a week (-10 points). Less severe but still not wanted.

* Higher scores indicate better timetables.

**Genetic Terms:**

* Fitness Function: Measures how good a chromosome (timetable) is.
---

## Author
**Conor Dawson**  
BSc (Hons) in Software Development 
