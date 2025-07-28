**QUERY**

**1)Creation of Database names cricket\_db.**

CREATE DATABASE IF NOT EXISTS cricket\_db;

USE cricket\_db;



**2)Creation of Teams Table.**

CREATE TABLE IF NOT EXISTS Teams (

TeamID INT AUTO\_INCREMENT PRIMARY KEY, TeamName VARCHAR(100) NOT NULL,

CoachName VARCHAR(100), Captain VARCHAR(100));



**3)Creation of CricketPlayers Table.**

CREATE TABLE IF NOT EXISTS CricketPlayers ( PlayerID INT AUTO\_INCREMENT PRIMARY KEY, FullName VARCHAR(100) NOT NULL,

Age INT,

Role VARCHAR(50), TeamID INT,

FOREIGN KEY (TeamID) REFERENCES Teams(TeamID) ON DELETE CASCADE

);



**4)Creation of Matches Table.**

CREATE TABLE IF NOT EXISTS Matches (

MatchID INT AUTO\_INCREMENT PRIMARY KEY,

MatchDate DATE, Team1ID INT, Team2ID INT,

Venue VARCHAR(100),

WinnerTeamID INT NULL,

FOREIGN KEY (Team1ID) REFERENCES Teams(TeamID) ON DELETE CASCADE,

FOREIGN KEY (Team2ID) REFERENCES Teams(TeamID) ON DELETE CASCADE,

FOREIGN KEY (WinnerTeamID) REFERENCES Teams(TeamID) ON DELETE SET NULL);



**5)Join table to displaying the details.**

SELECT cp.FullName AS PlayerName, t.TeamName, t.Captain FROM CricketPlayers cp

JOIN Teams t ON cp.TeamID = t.TeamID;



**6)Updating winner.**

UPDATE Matches

SET WinnerTeamID = 1 WHERE MatchID = 2;



