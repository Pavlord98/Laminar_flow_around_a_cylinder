<h1>Simulation of flows past a cylinder at various values of Reynolds number with OpenFOAM</h1>

This set of simulations consists of 4 simulations that use the same geometry and mesh, but different values of the kinematic visosity $\mu$\, and thus achieving different values for the Reynolds number in accordance with its definition:
$Re=UD/\mu $.

Flow around a cylinder and the phenomenae that occur at various values of <strong><em>Re</em></strong> is a well known canonical case in fluid mechanics. I did theese simulations to solidify what i learned about CFD and get some practice in OpenFOAM. I ran simulations at <strong><em>Re</em></strong> values of: 2, 20, 100 and 4400. The following image found in [this paper](https://www.researchgate.net/publication/282655240_Effect_of_Free_stream_turbulence_on_flow_past_a_circular_cylinder) ilustrates the resulting phenomenae.

<p align="center">
  <img src="https://github.com/Pavlord98/OpenFOAM-simulations/blob/main/Flow%20past%20a%20circular%20cylinder/1-Flow-past-a-circular-cylinder-at-different-Reynolds-number.png" alt="Flow past a circular cylinder at different Reynolds number"/>
</p>

### Geometry and Mesh
Because of the simplicity of the geometry, I constructed it and its mesh using just BlockMesh. I divided the mesh into regions in the way shown in the picture below.
<p align="center">
  <img src="https://github.com/Pavlord98/OpenFOAM-simulations/blob/main/Flow%20past%20a%20circular%20cylinder/mesh_zones.png" alt="Flow past a circular cylinder at different Reynolds number"/>
</p>
The mesh density is greater in the zones close to the cylinder and in the zones where the trailing wake is expected to be. I also used simple grading to create finer meshing in the most important regions. The mesh has later on proven to be adequate in resolotion in the wake regions and has also achieved the adequate values of y<sup>+</sup> for the wall functions i used in the turbulent case.

### Model setup

For the laminar cases I used the icoFoam solver and the pisoFoam solver for the turbulent case. The discretization schemes i used are fairly standard and can be found in the fvsSchemes dictionary. The same can be said for fvSolution. I used Scotch decomposition to split the domain into 8 parts and ran the simulations on my AMD FX-8320 CPU which were completed in reasonable time (less than 20 minutes for each). 

### Results
