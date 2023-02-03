<h1>Simulation of flows past a cylinder at various values of Reynolds number with OpenFOAM</h1>

This set of simulations consists of 4 simulations that use the same geometry and mesh, but different values of the kinematic visosity $\mu$\, and thus achieving different values for the Reynolds number in accordance with its definition:
$Re=UD/\mu $.

Flow around a cylinder and the phenomenae that occur at various values of <strong><em>Re</em></strong> is a well known canonical case in fluid mechanics. I did theese simulations to solidify what i learned about CFD and get some practice in OpenFOAM. I ran simulations at <strong><em>Re</em></strong> values of: 1, 20, 55 and 100. The following image found in [this paper](https://www.researchgate.net/publication/282655240_Effect_of_Free_stream_turbulence_on_flow_past_a_circular_cylinder) ilustrates the resulting phenomenae.

<p align="center">
  <img src="https://github.com/Pavlord98/OpenFOAM-simulations/blob/main/Flow%20past%20a%20circular%20cylinder/1-Flow-past-a-circular-cylinder-at-different-Reynolds-number.png" alt="Flow past a circular cylinder at different Reynolds number"/>
</p>

### Geometry and Mesh
Because of the simplicity of the geometry, I constructed it and its mesh using just BlockMesh. I divided the mesh into regions in the way shown in the picture below.
<p align="center">
  <img src="https://github.com/Pavlord98/OpenFOAM-simulations/blob/main/Flow%20past%20a%20circular%20cylinder/mesh_zones.png" alt="Flow past a circular cylinder at different Reynolds number"/>
</p>
The mesh density is greater in the zones close to the cylinder and in the zones where the trailing wake is expected to be. I also used simple grading to create finer meshing in the most important regions.

### Model setup

I used the icoFoam solver for all of the cases. The discretization schemes i used are fairly standard and can be found in the fvsSchemes dictionary. The same can be said for fvSolution. I used Scotch decomposition to split the domain into 8 parts and ran the simulations on my AMD FX-8320 CPU which were completed in reasonable time (less than 20 minutes for each). 

### Results

I visualized the results with the following animation which presents one seceond of the simulations with the first 0.1 seconds playing in a slower speed.

https://user-images.githubusercontent.com/84512701/210332136-ad9c6c00-cc4c-4d1c-8e45-ef80d068108f.mp4

The resulst are as expected. For the lowest Reynolds number there is no backflow. In the case in which the Reynolds number was 20 a steady backflow appears. At the Reynolds number of 55, we can see unsteady shedding of the flow, and at 100 we can see a fully devoloped Karman street.


I also made an animation of the case with a reynold's number of 100 with particle tracing added on.

https://user-images.githubusercontent.com/84512701/216606894-19394950-64ee-462c-ac00-ccba4754bf51.mp4

