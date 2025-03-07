Project Outline:
- interested in using various subdivision algorithms to smoothen meshes for better processing and visuals
- curious as to how different existing algorithms compare with one another in terms of geometrical properties, runtime, memory space, etc.
- 

Project PAIN points: 
- attempted using C/C++ initially, but had problems with dependencies (whether to use MingGW 64, MSVC [for Microsoft VS], etc.)
- switched to conda instead but after updating python to 3.10 for thingi10k, ran into further dependency problems with vtk vedo 
- igl import error and conflicts 
- butterfly subdivision -> matching new vertex indices with those of new edges, laptop can't handle >7 iterations 

Learned info abt graphics:
- vedo, trimesh, matplotlib, or use igl.writeobj to turn into .obj file
- existing databases with irregular meshes:
    - RWTT (uses photo reconstruction methods, but subdivision algorithms can exacerbate the problem [too many vertices])
    - Digital michelangelo project (3D scanning of large figures, digitized 10 statues by Michelangelo)
    - Stanford 3D scanning repository (raw 3D scans) -> their zippering and volumetric range image merging methods produce smooth manifolds and alr reduce noise 
        - range imaging captures 3D shapes by measuring distance from sensor to object, reconstruct 3D model from partial scans
        - first step is align range image (each scan) in the same coordinate system, but still have gaps that don't fully connect so zipper them tgt -> hence not best for surface reconstruction 
        - unrelated but some 3D scanning techniques capture connectivity, so treating them as pt clouds (j xyz coord) is discarding useful information 
    - or use standard methodology like quadric edge collapse decimation and voxel-based remeshing 
- to test subdivision alg, either find database with irregular meshes or break down 
- gaussian and mean curvature (product of two principle curvatures, latter average of them), gives insight to local geometric properties (ellipse, saddle-like, etc.) -> gaussian pre-butt (-95870), post-butt (-1.6e+8) | mean pre-butt (0.2), post-butt (0)
- to test smoothness, find other metrics such as normal variation

Learned info abt cmd:
- cache is locally stored copies so calling thingi10k.init() won't re-download everything again/ allows downloads to resume
- wtv you can't install with conda, install with pip and vice versa
- there could be corrupted files, just uninstall and then re-install (polyscope)

Papers/datasets I took inspo from:
- https://graphics.stanford.edu/data/3Dscanrep/
- (unrelated but for surface construction) https://graphics.stanford.edu/courses/cs468-12-spring/LectureSlides/03_Surface_Reconstruction.pdf
- https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=99ca8274377ee438fbb748438aa3057e7f6654a2
- #   R n R 2 0 2 5  
 