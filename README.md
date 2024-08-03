<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Bouncing Shapes</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: red;
        }

        #container {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
</head>
<body>
    <div id="container"></div>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
     
        const container = document.getElementById('container');
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(renderer.domElement);

        const geometryCube = new THREE.BoxGeometry(1, 1, 1);
        const materialCube = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
        const cube1 = new THREE.Mesh(geometryCube, materialCube);
        const cube2 = new THREE.Mesh(geometryCube, materialCube);

        const geometrySphere = new THREE.SphereGeometry(0.5, 32, 32);
        const materialSphere = new THREE.MeshBasicMaterial({ color: 0x0000ff });
        const sphere1 = new THREE.Mesh(geometrySphere, materialSphere);
        const sphere2 = new THREE.Mesh(geometrySphere, materialSphere);

        scene.add(cube1);
        scene.add(cube2);
        scene.add(sphere1);
        scene.add(sphere2);

        camera.position.z = 5;

        let directionCube1 = 0.05;
        let directionCube2 = -0.05;
        let directionSphere1 = 0.05;
        let directionSphere2 = -0.05;

        function animate() {
            requestAnimationFrame(animate);

            if (cube1.position.x > 2 || cube1.position.x < -2) directionCube1 = -directionCube1;
            cube1.position.x += directionCube1;
            cube1.scale.x += directionCube1 * 0.1;
            cube1.scale.y += directionCube1 * 0.1;
            cube1.scale.z += directionCube1 * 0.1;

            if (cube2.position.x > 2 || cube2.position.x < -2) directionCube2 = -directionCube2;
            cube2.position.x += directionCube2;
            cube2.scale.x += directionCube2 * 0.1;
            cube2.scale.y += directionCube2 * 0.1;
            cube2.scale.z += directionCube2 * 0.1;

            if (sphere1.position.y > 2 || sphere1.position.y < -2) directionSphere1 = -directionSphere1;
            sphere1.position.y += directionSphere1;
            sphere1.scale.x += directionSphere1 * 0.1;
            sphere1.scale.y += directionSphere1 * 0.1;
            sphere1.scale.z += directionSphere1 * 0.1;

            if (sphere2.position.y > 2 || sphere2.position.y < -2) directionSphere2 = -directionSphere2;
            sphere2.position.y += directionSphere2;
            sphere2.scale.x += directionSphere2 * 0.1;
            sphere2.scale.y += directionSphere2 * 0.1;
            sphere2.scale.z += directionSphere2 * 0.1;

            renderer.render(scene, camera);
        }

        animate();
    </script>
</body>
</html>
