Let's start by figuring out how many dinosaurs we have. Count the number of dinosaurs.

SELECT COUNT(name) FROM dinos;

We want to open up our own version of Jurassic Park, but this time only with dinosaurs who are actually from the Jurassic period. Find all the dinosaurs from the Jurassic period.

SELECT name FROM dinos WHERE period='Jurassic';

Jurassic Park was a huge success for us. Now we want to open up a sequel park: Cretaceous Park. This time though, we're a little more organized, and we want to know how much space all these dinosaurs are going to take up. Find the total sum length of all the dinosaurs from the Cretaceous period.

SELECT SUM(length) FROM dinos WHERE period='Cretaceous';

Great news! Our board of investors recently secured us a large island where we can put all the dinosaurs from both Jurassic Park and Cretaceous Park. This new park will be called Juraceous Park, which according to our focus groups really rolls off the tongue. Find all the dinosaurs from either the Jurassic OR Cretaceous periods, and order them by their species name alphabetically.


SELECT name
FROM dinos
WHERE period='Jurassic' OR period='Cretaceous'
ORDER by species ASC;


Saurischians are the "lizard hipped" order of dinosaurs, and one of the two main branches. All carnivorous dinosaurs are Saurischians, but not all Saurischians are carnivorous. Find all the dinosaurs from the t_order Saurischia that are Herbivorous.


SELECT name
FROM dinos
WHERE t_order='Saurischia' AND diet='Herbivorous';

Dinosaur names are hard to remember. Find the shortest dinosaur, and rename it Shortie.


UPDATE dinos
SET name = 'Shortie'
WHERE length in (SELECT MIN(length) FROM dinos);

SELECT name
FROM dinos
WHERE length in (SELECT MIN(length) FROM dinos);

It's the first day of Dino School, and we're doing roll call. Find the alphabetically first dinosaur, so we can make sure they're present for class.


SELECT name
FROM dinos
ORDER by name ASC
LIMIT 1;

Rename the five longest dinosaurs The Famous Five.


UPDATE dinos
SET name = 'The Famous Five'
WHERE length in(SELECT length FROM dinos WHERE length > 0 ORDER BY length DESC LIMIT 5);

Check that it worked:
SELECT name
FROM dinos
WHERE length > 0
ORDER BY length DESC
LIMIT 5;
