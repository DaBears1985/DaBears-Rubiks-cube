<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rubik's Cube Simulator</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Initialize the scene, camera, and renderer
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        // Create a Rubik's Cube
        const cubeSize = 1;
        const colors = ['red', 'green', 'blue', 'yellow', 'white', 'orange'];
        const cubes = [];
        const group = new THREE.Group();

        for (let x = -1; x <= 1; x++) {
            for (let y = -1; y <= 1; y++) {
                for (let z = -1; z <= 1; z++) {
                    const geometry = new THREE.BoxGeometry(cubeSize, cubeSize, cubeSize);
                    const materials = colors.map(color => new THREE.MeshBasicMaterial({ color }));
                    const mesh = new THREE.Mesh(geometry, materials);
                    mesh.position.set(x * cubeSize, y * cubeSize, z * cubeSize);
                    group.add(mesh);
                    cubes.push(mesh);
                }
            }
        }
        scene.add(group);
        camera.position.z = 5;

        // Handle input for cube rotation
        const rotateCube = { x: 0, y: 0 };

        document.addEventListener('keydown', (event) => {
            switch (event.key) {
                case 'w':
                    rotateCube.x -= 0.1;
                    break;
                case 's':
                    rotateCube.x += 0.1;
                    break;
                case 'a':
                    rotateCube.y -= 0.1;
                    break;
                case 'd':
                    rotateCube.y += 0.1;
                    break;
                case 'ArrowUp':
                    group.rotation.x -= 0.1;
                    break;
                case 'ArrowDown':
                    group.rotation.x += 0.1;
                    break;
                case 'ArrowLeft':
                    group.rotation.y -= 0.1;
                    break;
                case 'ArrowRight':
                    group.rotation.y += 0.1;
                    break;
            }
        });

        // Animation loop
        function animate() {
            requestAnimationFrame(animate);
            group.rotation.x += rotateCube.x;
            group.rotation.y += rotateCube.y;
            renderer.render(scene, camera);
        }
        animate();
    </script>
</body>
</html>
