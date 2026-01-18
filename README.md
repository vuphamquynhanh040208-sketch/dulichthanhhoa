<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Khám Phá Du Lịch Ảo Thanh Hóa</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script> <!-- Nhúng Three.js -->
</head>
<body>
    <header>
        <h1>Khám Phá Du Lịch Ảo Thanh Hóa</h1>
        <nav>
            <a href="#home">Trang Chủ</a>
            <a href="#gems">Hidden Gems</a>
            <a href="#blog">Blog</a>
            <a href="#contact">Liên Hệ</a>
        </nav>
    </header>
    
    <section id="home">
        <h2>Chào Mừng Đến Với Du Lịch Ảo Thanh Hóa</h2>
        <p>Khám phá những bí mật ít người biết đến qua hình ảnh 3D sống động. Dự án của học sinh lớp 12!</p>
        <div id="3d-container" style="width: 600px; height: 400px; margin: 0 auto; border: 1px solid #ccc;"></div> <!-- Container cho 3D -->
    </section>
    
    <section id="gems">
        <h2>Hidden Gems Thanh Hóa</h2>
        <div class="gem">
            <h3>Làng Pù Luông</h3>
            <p>Mô tả: Làng quê yên bình với thác nước. Khám phá qua 3D!</p>
            <div id="gem-3d" style="width: 400px; height: 300px; margin: 0 auto; border: 1px solid #ccc;"></div> <!-- Container 3D cho gem -->
        </div>
        <!-- Thêm gem khác nếu muốn -->
    </section>
    
    <footer>
        <p>&copy; 2023 Dự Án Học Sinh. Liên Hệ: email@example.com</p>
    </footer>

    <script>
        // Mã Three.js: Tạo scene, camera, renderer
        function init3D(containerId, textureUrl) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, 600 / 400, 0.1, 1000); // Điều chỉnh tỷ lệ
            const renderer = new THREE.WebGLRenderer();
            renderer.setSize(600, 400);
            document.getElementById(containerId).appendChild(renderer.domElement);

            // Tạo geometry (hình dạng) - Khối lập phương đại diện cho địa điểm
            const geometry = new THREE.BoxGeometry(1, 1, 1);

            // Tải texture từ ảnh (thay 'texture.jpg' bằng URL ảnh của bạn)
            const textureLoader = new THREE.TextureLoader();
            const texture = textureLoader.load(textureUrl); // URL ảnh texture
            const material = new THREE.MeshBasicMaterial({ map: texture });

            const cube = new THREE.Mesh(geometry, material);
            scene.add(cube);

            camera.position.z = 5;

            // Hàm animate: Xoay mô hình
            function animate() {
                requestAnimationFrame(animate);
                cube.rotation.x += 0.01;
                cube.rotation.y += 0.01;
                renderer.render(scene, camera);
            }
            animate();

            // Thêm điều khiển: Xoay bằng chuột (tùy chọn nâng cao)
            const controls = new THREE.OrbitControls(camera, renderer.domElement);
            controls.enableDamping = true;
            controls.dampingFactor = 0.05;
        }

        // Khởi tạo 3D cho trang chủ (thay URL ảnh bằng link thực tế, ví dụ: upload ảnh lên GitHub và dùng raw link)
        init3D('3d-container', 'https://raw.githubusercontent.com/[tên-github-của-bạn]/du-lich-ao-thanh-hoa/main/texture.jpg'); // Thay bằng link ảnh

        // Khởi tạo 3D cho gem (có thể dùng ảnh khác)
        init3D('gem-3d', 'https://raw.githubusercontent.com/[tên-github-của-bạn]/du-lich-ao-thanh-hoa/main/texture2.jpg');
    </script>
</body>
</html># dulichthanhhoa
