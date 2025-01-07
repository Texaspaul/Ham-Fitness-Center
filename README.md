TriathlonResults
Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package TexasTriathlonResults;

/**
 *
 * @author Texas
 */
public class TriathlonResults {
    
     public class TriathlonResults 
     {
    private final String name;
    private final int id;
    private final int swimmingTime; // in seconds
    private final int cyclingTime;   // in seconds
    private final int runningTime;   // in seconds

    public TriathlonResults(String name, int id, int swimmingTime, int cyclingTime, int runningTime) {
        if (swimmingTime < 0 || cyclingTime < 0 || runningTime < 0) {
            throw new IllegalArgumentException("Time values must be non-negative.");
        }
        this.name = name;
        this.id = id;
        this.swimmingTime = swimmingTime;
        this.cyclingTime = cyclingTime;
        this.runningTime = runningTime;
    }

    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }

    public int getSwimmingTime() {
        return swimmingTime;
    }

    public int getCyclingTime() {
        return cyclingTime;
    }

    public int getRunningTime() {
        return runningTime;
    }

    @Override
    public String toString() {
        return "TriathlonResults{" +
                "name='" + name + '\'' +
                ", id=" + id +
                ", swimmingTime=" + swimmingTime +
                ", cyclingTime=" + cyclingTime +
                ", runningTime=" + runningTime +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof TriathlonResults)) return false;
        TriathlonResults that = (TriathlonResults) o;
        return id == that.id &&
                swimmingTime == that.swimmingTime &&
                cyclingTime == that.cyclingTime &&
                runningTime == that.runningTime &&
                name.equals(that.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, id, swimmingTime, cyclingTime, runningTime);
    }
}


}




Participants

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package TexasTriathlonResults;

/**
 *
 * @author Texas
 */
public class Participants {
    public class Participant extends TriathlonResults {

    public Participant(String name, int id, int swimmingTime, int cyclingTime, int runningTime) {

        super(name, id, swimmingTime, cyclingTime, runningTime);

        validateTimes(swimmingTime, cyclingTime, runningTime);

    }


    private void validateTimes(int swimmingTime, int cyclingTime, int runningTime) {

        if (swimmingTime < 0 || cyclingTime < 0 || runningTime < 0) {

            throw new IllegalArgumentException("Time values must be non-negative.");

        }

    }


    public int getTotalTime() {

        return getSwimmingTime() + getCyclingTime() + getRunningTime(); // Total time in seconds

    }


    public void displayDetails() {

        System.out.println("Name: " + getName() + ", ID: " + getId() + ", Total Time: " + getTotalTime() + " seconds");

    }

}


public class EliteParticipant extends Participant {

    private String sponsorName;


    public EliteParticipant(String name, int id, int swimmingTime, int cyclingTime, int runningTime, String sponsorName) {

        super(name, id, swimmingTime, cyclingTime, runningTime);

        if (sponsorName == null || sponsorName.isEmpty()) {

            throw new IllegalArgumentException("Sponsor name cannot be null or empty.");

        }

        this.sponsorName = sponsorName;

    }


    @Override

    public void displayDetails() {

        super.displayDetails();

        System.out.println("Sponsor: " + sponsorName);

    }

}


public class BeginnerParticipant extends Participant {

    public BeginnerParticipant(String name, int id, int swimmingTime, int cyclingTime, int runningTime) {

        super(name, id, swimmingTime, cyclingTime, runningTime);

    }
