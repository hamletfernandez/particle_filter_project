# particle_filter_project | Team Members: Hamlet Fernandez

## Implementation Plan 

### How you will initialize your particle cloud (initialize_particle_cloud)?
I hope to use a for loop that will push particles p into the particle_cloud list. These particles can be initialized using the self.num_particles value with Point locations respective to the Occupancy Grid and map.
### How you will update the position of the particles will be updated based on the movements of the robot (update_particles_with_motion_model)?
Translations of each of the particles' pose coordinates with respect to their orientation. This part will follow a similar structure to the "Move" section of the Monte Carlo Localizaton exercise we did in class. 
### How you will compute the importance weights of each particle after receiving the robot's laser scan data?(update_particle_weights_with_measurement_model)?
We have the *x*, *y*, and *z* values of each particles from their pose, and we have data in the form of self.laserpose which will act as our sensor readings. Using the data read from the *left*, *front*, and *right* sensors of the turtlebot we will compute weights like $\frac{1}{|left - x| + |front - y| + |right - z|}$
### How you will normalize the particles' importance weights (normalize_particles) and resample the particles (resample_particles)?
I will use aloop to sum all the current weights of all particles and then divide each of their weights by the sum. To resample, I might choose a cutoff point (?) such that I delete half the particles with normalized weights less than the median. 
### How you will update the estimated pose of the robot (update_estimated_robot_pose)?
I can pick a random pose from the partices left after resampling and use that pose for the turtlebot. As the sample of possible particles gets smaller, so does the window of error. 
### How you will incorporate noise into your particle filter localization?
By adjusting the cutoff point for resampling to include more particles than necessary. This will give us room for errors we make in not considering noise. 