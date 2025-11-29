<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบติดตามผลการเรียน</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #dbeafe 0%, #e0e7ff 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .header {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        .header h1 {
            color: #1e3a8a;
            font-size: 32px;
            margin-bottom: 10px;
        }

        .header p {
            color: #666;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 12px;
            margin-bottom: 20px;
        }

        .stat-card {
            padding: 15px;
            border-radius: 8px;
            border: 2px solid;
            background-color: #f0f9ff;
            text-align: center;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .stat-card:hover {
            transform: translateY(-2px);
        }

        .stat-card.blue { border-color: #3b82f6; }
        .stat-card.gray { border-color: #d1d5db; }
        .stat-card.green { border-color: #22c55e; background-color: #f0fdf4; }
        .stat-card.orange { border-color: #f97316; background-color: #fff7ed; }
        .stat-card.red { border-color: #ef4444; background-color: #fef2f2; }
        .stat-card.purple { border-color: #a855f7; background-color: #faf5ff; }

        .stat-number {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .stat-card.blue .stat-number { color: #2563eb; }
        .stat-card.gray .stat-number { color: #6b7280; }
        .stat-card.green .stat-number { color: #22c55e; }
        .stat-card.orange .stat-number { color: #f97316; }
        .stat-card.red .stat-number { color: #ef4444; }
        .stat-card.purple .stat-number { color: #a855f7; }

        .stat-label {
            font-size: 12px;
            color: #666;
        }

        .controls {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        .button-group {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }

        button {
            padding: 10px 20px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: background 0.2s;
        }

        .btn-primary {
            background: #4f46e5;
            color: white;
        }

        .btn-primary:hover {
            background: #4338ca;
        }

        .btn-success {
            background: #22c55e;
            color: white;
        }

        .btn-success:hover {
            background: #16a34a;
        }

        .btn-secondary {
            background: #e5e7eb;
            color: #333;
        }

        .btn-secondary:hover {
            background: #d1d5db;
        }

        .btn-danger {
            background: #ef4444;
            color: white;
            padding: 5px 10px;
            font-size: 12px;
        }

        .filters {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }

        .filter-group {
            display: flex;
            flex-direction: column;
        }

        label {
            font-size: 13px;
            font-weight: 600;
            color: #333;
            margin-bottom: 5px;
        }

        select, input {
            padding: 8px 12px;
            border: 1px solid #d1d5db;
            border-radius: 6px;
            font-size: 14px;
        }

        select:focus, input:focus {
            outline: none;
            border-color: #4f46e5;
            box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.1);
        }

        .student-list {
            display: grid;
            gap: 15px;
        }

        .student-card {
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .student-header {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            background: #f9fafb;
            border-bottom: 1px solid #e5e7eb;
        }

        .student-header:hover {
            background: #f3f4f6;
        }

        .student-info {
            flex: 1;
        }

        .student-name {
            font-weight: bold;
            font-size: 16px;
            color: #1f2937;
        }

        .student-detail {
            font-size: 13px;
            color: #666;
            margin-top: 3px;
        }

        .student-stats {
            display: flex;
            gap: 30px;
            align-items: center;
        }

        .stat-item {
            text-align: right;
        }

        .stat-item-value {
            font-size: 20px;
            font-weight: bold;
            color: #2563eb;
        }

        .stat-item-label {
            font-size: 12px;
            color: #666;
        }

        .student-actions {
            display: flex;
            gap: 10px;
        }

        .btn-icon {
            width: 40px;
            height: 40px;
            padding: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 6px;
            font-size: 20px;
        }

        .btn-edit {
            background: #e0e7ff;
            color: #2563eb;
        }

        .btn-delete {
            background: #fee2e2;
            color: #ef4444;
        }

        .student-subjects {
            padding: 20px;
            background: #f9fafb;
            border-top: 1px solid #e5e7eb;
        }

        .subjects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 12px;
        }

        .subject-item {
            background: white;
            padding: 12px;
            border-radius: 6px;
            border: 1px solid #e5e7eb;
        }

        .subject-name {
            font-weight: 600;
            color: #1f2937;
            margin-bottom: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .status-badge {
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 11px;
            font-weight: 600;
        }

        .status-0 { background: #f3f4f6; color: #4b5563; }
        .status-r { background: #dcfce7; color: #166534; }
        .status-ms { background: #fed7aa; color: #92400e; }
        .status-mp { background: #fecaca; color: #991b1b; }

        .subject-info {
            font-size: 12px;
            color: #666;
        }

        .hidden {
            display: none;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: 8px;
            max-width: 600px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
            padding: 30px;
        }

        .modal-title {
            font-size: 24px;
            font-weight: bold;
            color: #1e3a8a;
            margin-bottom: 20px;
        }

        .form-section {
            background: #dbeafe;
            padding: 15px;
            border-radius: 6px;
            margin-bottom: 20px;
        }

        .form-section h3 {
            font-size: 14px;
            font-weight: 600;
            color: #333;
            margin-bottom: 12px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 12px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group input,
        .form-group select {
            width: 100%;
        }

        .modal-actions {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .modal-actions button {
            flex: 1;
            padding: 12px;
        }

        .footer {
            text-align: center;
            color: #666;
            font-size: 13px;
            margin-top: 30px;
        }

        .corrected-list {
            max-height: 500px;
            overflow-y: auto;
        }

        .corrected-item {
            background: #faf5ff;
            padding: 15px;
            border-radius: 6px;
            border: 1px solid #e9d5ff;
            margin-bottom: 12px;
        }

        .corrected-item h4 {
            color: #6b21a8;
            margin-bottom: 8px;
        }

        .corrected-item p {
            font-size: 12px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>ระบบติดตามผลการเรียน</h1>
            <p>ติดตามสถานะการเรียน เกรด 0, ร, มส, มผ ของนักเรียนในแต่ละวิชา</p>
        </div>

        <!-- Stats -->
        <div class="stats">
            <div class="stat-card blue">
                <div class="stat-number" id="stat-total">2</div>
                <div class="stat-label">จำนวนนักเรียน</div>
            </div>
            <div class="stat-card gray">
                <div class="stat-number" id="stat-grade0">1</div>
                <div class="stat-label">เกรด 0</div>
            </div>
            <div class="stat-card green">
                <div class="stat-number" id="stat-r">2</div>
                <div class="stat-label">ร (รอผล)</div>
            </div>
            <div class="stat-card orange">
                <div class="stat-number" id="stat-ms">0</div>
                <div class="stat-label">มส (ไม่มีสิทธิ)</div>
            </div>
            <div class="stat-card red">
                <div class="stat-number" id="stat-mp">0</div>
                <div class="stat-label">มผ (ไม่ผ่าน)</div>
            </div>
            <div class="stat-card purple" onclick="showCorrectedModal()">
                <div class="stat-number" id="stat-corrected">0</div>
                <div class="stat-label">แก้ไขแล้ว</div>
            </div>
        </div>

        <!-- Controls -->
        <div class="controls">
            <div class="button-group">
                <button class="btn-primary" onclick="showAddForm()">➕ เพิ่มนักเรียน</button>
                <button class="btn-success" onclick="exportCSV()">⬇️ ส่งออก CSV</button>
            </div>
            <div class="filters">
                <div class="filter-group">
                    <label>ห้อง</label>
                    <select id="filterClass" onchange="updateDisplay()">
                        <option value="">ทั้งหมด</option>
                        <option value="4/1">4/1</option>
                        <option value="4/2">4/2</option>
                    </select>
                </div>
                <div class="filter-group">
                    <label>ครูที่ปรึกษา</label>
                    <select id="filterAdvisor" onchange="updateDisplay()">
                        <option value="">ทั้งหมด</option>
                        <option value="ครูเอก">ครูเอก</option>
                    </select>
                </div>
            </div>
        </div>

        <!-- Student List -->
        <div class="student-list" id="studentList"></div>

        <!-- Footer -->
        <div class="footer">
            <p>ระบบติดตามผลการเรียน - ฝ่ายบริหารวิชาการ</p>
        </div>
    </div>

    <!-- Add/Edit Modal -->
    <div id="formModal" class="modal">
        <div class="modal-content">
            <div class="modal-title" id="formTitle">เพิ่มนักเรียนใหม่</div>

            <div class="form-section">
                <h3>ข้อมูลพื้นฐาน</h3>
                <div class="form-grid">
                    <div class="form-group">
                        <label>ชื่อนักเรียน</label>
                        <input type="text" id="inputName" placeholder="ชื่อนักเรียน">
                    </div>
                    <div class="form-group">
                        <label>ห้อง (เช่น ม.3/1)</label>
                        <input type="text" id="inputClass" placeholder="ห้อง">
                    </div>
                    <div class="form-group">
                        <label>ครูที่ปรึกษา</label>
                        <input type="text" id="inputAdvisor" placeholder="ครูที่ปรึกษา">
                    </div>
                </div>
            </div>

            <div class="form-section">
                <h3>รายวิชาที่ติด</h3>
                <div style="margin-bottom: 15px;">
                    <div class="form-grid" style="grid-template-columns: 1fr 1fr 1fr 1fr auto;">
                        <input type="text" id="inputSubjectName" placeholder="ชื่อวิชา">
                        <select id="inputSubjectStatus">
                            <option value="0">เกรด 0</option>
                            <option value="ร">ร (รอผล)</option>
                            <option value="มส">มส (ไม่มีสิทธิ)</option>
                            <option value="มผ">มผ (ไม่ผ่าน)</option>
                        </select>
                        <input type="text" id="inputTeacher" placeholder="ครูผู้สอน">
                        <button class="btn-primary" onclick="addSubject()">เพิ่ม</button>
                    </div>
                </div>
                <div id="subjectsList"></div>
            </div>

            <div class="modal-actions">
                <button class="btn-secondary" onclick="closeModal()">ยกเลิก</button>
                <button class="btn-primary" onclick="saveStudent()">บันทึกข้อมูล</button>
            </div>
        </div>
    </div>

    <!-- Corrected Modal -->
    <div id="correctedModal" class="modal">
        <div class="modal-content">
            <div class="modal-title">รายการนักเรียนที่แก้ไขแล้ว</div>
            <div class="corrected-list" id="correctedList"></div>
            <div class="modal-actions" style="margin-top: 20px;">
                <button class="btn-primary" onclick="closeCorrectedModal()" style="flex: 1;">ปิด</button>
            </div>
        </div>
    </div>

    <script>
        let students = [
            {
                id: 1,
                name: 'นักเรียน ก',
                classRoom: '4/1',
                advisor: 'ครูเอก',
                subjects: [
                    { id: 1, name: 'คณิตศาสตร์', status: 'ร', teacher: 'ครูสมชาย' },
                    { id: 2, name: 'วิทยาศาสตร์', status: '0', teacher: 'ครูสมนึก' }
                ]
            },
            {
                id: 2,
                name: 'นักเรียน ข',
                classRoom: '4/1',
                advisor: 'ครูเอก',
                subjects: [
                    { id: 1, name: 'คณิตศาสตร์', status: 'ร', teacher: 'ครูสมชาย' }
                ]
            }
        ];

        let currentEditingId = null;
        let currentSubjects = [];

        function updateStats() {
            const filtered = getFilteredStudents();
            const total = filtered.length;
            const grade0 = filtered.filter(s => s.subjects.some(sub => sub.status === '0')).length;
            const r = filtered.filter(s => s.subjects.some(sub => sub.status === 'ร')).length;
            const ms = filtered.filter(s => s.subjects.some(sub => sub.status === 'มส')).length;
            const mp = filtered.filter(s => s.subjects.some(sub => sub.status === 'มผ')).length;
            const corrected = filtered.filter(s => {
                const hasStatus = s.subjects.some(sub => ['0', 'มส', 'มผ'].includes(sub.status));
                const hasR = s.subjects.some(sub => sub.status === 'ร');
                return hasStatus && hasR;
            }).length;

            document.getElementById('stat-total').textContent = total;
            document.getElementById('stat-grade0').textContent = grade0;
            document.getElementById('stat-r').textContent = r;
            document.getElementById('stat-ms').textContent = ms;
            document.getElementById('stat-mp').textContent = mp;
            document.getElementById('stat-corrected').textContent = corrected;
        }

        function getFilteredStudents() {
            const classFilter = document.getElementById('filterClass').value;
            const advisorFilter = document.getElementById('filterAdvisor').value;
            return students.filter(s =>
                (!classFilter || s.classRoom === classFilter) &&
                (!advisorFilter || s.advisor === advisorFilter)
            );
        }

        function updateDisplay() {
            const filtered = getFilteredStudents();
            const list = document.getElementById('studentList');
            list.innerHTML = filtered.map(student => `
                <div class="student-card">
                    <div class="student-header" onclick="toggleSubjects('${student.id}')">
                        <div class="student-info">
                            <div class="student-name">${student.name}</div>
                            <div class="student-detail">ห้อง ${student.classRoom} | ${student.advisor}</div>
                        </div>
                        <div class="student-stats">
                            <div class="stat-item">
                                <div class="stat-item-value">${student.subjects.length}</div>
                                <div class="stat-item-label">วิชาทั้งหมด</div>
                            </div>
                        </div>
                        <div class="student-actions">
                            <button class="btn-icon btn-edit" onclick="editStudent(${student.id}, event)">✏️</button>
                            <button class="btn-icon btn-delete" onclick="deleteStudent(${student.id}, event)">🗑️</button>
                        </div>
                    </div>
                    <div id="subjects-${student.id}" class="student-subjects hidden">
                        <div class="subjects-grid">
                            ${student.subjects.map(sub => `
                                <div class="subject-item">
                                    <div class="subject-name">
                                        ${sub.name}
                                        <span class="status-badge status-${sub.status}">${sub.status}</span>
                                    </div>
                                    <div class="subject-info">ครูผู้สอน: ${sub.teacher || '-'}</div>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                </div>
            `).join('');
            updateStats();
        }

        function toggleSubjects(studentId) {
            const el = document.getElementById(`subjects-${studentId}`);
            el.classList.toggle('hidden');
        }

        function showAddForm() {
            currentEditingId = null;
            currentSubjects = [];
            document.getElementById('formTitle').textContent = 'เพิ่มนักเรียนใหม่';
            document.getElementById('inputName').value = '';
            document.getElementById('inputClass').value = '';
            document.getElementById('inputAdvisor').value = '';
            document.getElementById('subjectsList').innerHTML = '';
            document.getElementById('formModal').classList.add('active');
        }

        function editStudent(id, event) {
            event.stopPropagation();
            const student = students.find(s => s.id === id);
            if (!student) return;

            currentEditingId = id;
            currentSubjects = JSON.parse(JSON.stringify(student.subjects));
            document.getElementById('formTitle').textContent = 'แก้ไขข้อมูลนักเรียน';
            document.getElementById('inputName').value = student.name;
            document.getElementById('inputClass').value = student.classRoom;
            document.getElementById('inputAdvisor').value = student.advisor;
            renderSubjectsList();
            document.getElementById('formModal').classList.add('active');
        }

        function addSubject() {
            const name = document.getElementById('inputSubjectName').value;
            const status = document.getElementById('inputSubjectStatus').value;
            const teacher = document.getElementById('inputTeacher').value;

            if (!name) {
                alert('กรุณากรอกชื่อวิชา');
                return;
            }

            currentSubjects.push({ id: Date.now(), name, status, teacher });
            document.getElementById('inputSubjectName').value = '';
            document.getElementById('inputTeacher').value = '';
            renderSubjectsList();
        }

        function removeSubject(id) {
            currentSubjects = currentSubjects.filter(s => s.id !== id);
            renderSubjectsList();
        }

        function renderSubjectsList() {
            const list = document.getElementById('subjectsList');
            list.innerHTML = currentSubjects.map(sub => `
                <div style="display: flex; justify-content: space-between; background: white; padding: 10px; border-radius: 6px; border: 1px solid #e5e7eb; margin-bottom: 8px;">
                    <div>
                        <div style="font-weight: 600; color: #1f2937;">${sub.name}</div>
                        <div style="font-size: 12px; color: #666;">ครูผู้สอน: ${sub.teacher || '-'}</div>
                    </div>
                    <div style="display: flex; align-items: center; gap: 8px;">
                        <span class="status-badge status-${sub.status}">${sub.status}</span>
                        <button class="btn-danger" onclick="removeSubject(${sub.id})">ลบ</button>
                    </div>
                </div>
            `).join('');
        }

        function saveStudent() {
            const name = document.getElementById('inputName').value;
            const classRoom = document.getElementById('inputClass').value;
            const advisor = document.getElementById('inputAdvisor').value;

            if (!name || !classRoom || !advisor) {
                alert('กรุณากรอกข้อมูลให้ครบถ้วน');
                return;
            }

            if (currentEditingId) {
                const idx = students.findIndex(s => s.id === currentEditingId);
                if (idx !== -1) {
                    students[idx] = { id: currentEditingId, name, classRoom, advisor, subjects: currentSubjects };
                }
            } else {
                students.push({ id: Date.now(), name, classRoom, advisor, subjects: currentSubjects });
            }

            closeModal();
            updateDisplay();
        }

        function deleteStudent(id, event) {
            event.stopPropagation();
            if (confirm('ต้องการลบข้อมูลนักเรียนนี้หรือไม่?')) {
                students = students.filter(s => s.id !== id);
                updateDisplay();
            }
        }

        function showCorrectedModal() {
            const filtered = getFilteredStudents();
            const corrected = filtered.filter(s => {
                const hasStatus = s.subjects.some(sub => ['0', 'มส', 'มผ'].includes(sub.status));
                const hasR = s.subjects.some(sub => sub.status === 'ร');
                return hasStatus && hasR;
            });

            const list = document.getElementById('correctedList');
            if (corrected.length === 0) {
                list.innerHTML = '<p style="text-align: center; padding: 40px; color: #999;">ไม่มีรายการนักเรียนที่แก้ไขแล้ว</p>';
            } else {
                list.innerHTML = corrected.map(s => `
                    <div class="corrected-item">
                        <h4>${s.name} (ห้อง ${s.classRoom})</h4>
                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 10px;">
                            ${s.subjects.map(sub => `
                                <div style="padding: 8px; background: white; border-radius: 4px; border: 1px solid #e9d5ff;">
                                    <div style="font-weight: 600; font-size: 13px;">${sub.name}</div>
                                    <span class="status-badge status-${sub.status}">${sub.status}</span>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `).join('');
            }
            document.getElementById('correctedModal').classList.add('active');
        }

        function closeCorrectedModal() {
            document.getElementById('correctedModal').classList.remove('active');
        }

        function closeModal() {
            document.getElementById('formModal').classList.remove('active');
        }

        function exportCSV() {
            const filtered = getFilteredStudents();
            let csv = 'ลำดับ,ชื่อนักเรียน,ห้อง,ครูที่ปรึกษา,วิชา,สถานะ,ครูผู้สอน\n';
            
            filtered.forEach((s, i) => {
                if (s.subjects.length > 0) {
                    s.subjects.forEach((sub, j) => {
                        csv += `${j === 0 ? i + 1 : ''},"${s.name}","${s.classRoom}","${s.advisor}","${sub.name}","${sub.status}","${sub.teacher || '-'}"\n`;
                    });
                } else {
                    csv += `${i + 1},"${s.name}","${s.classRoom}","${s.advisor}","-","-","-"\n`;
                }
            });

            const link = document.createElement('a');
            link.href = 'data:text/csv;charset=utf-8,%EF%BB%BF' + encodeURIComponent(csv);
            link.download = 'students_tracking.csv';
            link.click();
        }

        // Initialize
        updateDisplay();
    </script>
</body>
</html>
