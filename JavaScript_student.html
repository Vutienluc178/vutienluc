<!-- JavaScript_student.html -->
<script>
// Data demo: lưu local, bạn có thể tích hợp backend sau
let students = [];
let diaryData = {};    // { studentId: [{date, subject, score, note}], ... }
let disciplineData = {}; // { studentId: [{date, type, note}], ... }
let currentUser = {name: "Giáo viên", role: "Admin"}; // demo login cứng

let currentPage = "dashboard";
let selectedStudentId = null;
let isEditingStudent = false;
let editingStudentId = null;

document.addEventListener('DOMContentLoaded', function() {
    initializeApp();
});

function initializeApp() {
    showLoading(true);

    // Setup event listeners
    setupEventListeners();

    // Fake data lần đầu nếu chưa có
    if (!localStorage.getItem('students')) {
        generateDemoData();
    }
    loadAllData();

    // UI
    updateCurrentDate();
    populateMonthYearSelects();
    updateAllClassFilters();
    showMainApp();

    showLoading(false);
}

function setupEventListeners() {
    // Navigation
    document.querySelectorAll('.nav-item').forEach(item => {
        item.addEventListener('click', function(e) {
            e.preventDefault();
            navigateToPage(this.dataset.page);
        });
    });

    document.getElementById('menuToggle').addEventListener('click', toggleSidebar);
    document.getElementById('navClose').addEventListener('click', closeSidebar);
    document.getElementById('overlay').addEventListener('click', closeSidebar);
    document.getElementById('refreshBtn').addEventListener('click', reloadPage);

    // Dashboard filters
    document.getElementById('dashboardClassFilter').addEventListener('change', updateDashboard);
    document.getElementById('dashboardMonth').addEventListener('change', updateDashboard);
    document.getElementById('dashboardYear').addEventListener('change', updateDashboard);

    // Diary filters
    document.getElementById('diaryClassFilter').addEventListener('change', updateDiaryClassStudents);
    document.getElementById('diaryStudentSelect').addEventListener('change', function() {
        selectedStudentId = this.value;
        renderDiaryPage();
    });

    // Statistics filters
    document.getElementById('statsClass').addEventListener('change', updateStatistics);
    document.getElementById('statsMonth').addEventListener('change', updateStatistics);
    document.getElementById('statsYear').addEventListener('change', updateStatistics);

    // Student page
    document.getElementById('addStudentBtn').addEventListener('click', openAddStudentModal);
    document.getElementById('studentSearch').addEventListener('input', searchStudents);

    // Student modal
    document.getElementById('modalClose').addEventListener('click', closeStudentModal);
    document.getElementById('modalCancel').addEventListener('click', closeStudentModal);
    document.getElementById('modalSave').addEventListener('click', saveStudent);

    // Confirm modal
    document.getElementById('confirmModalClose').addEventListener('click', closeConfirmModal);
    document.getElementById('confirmCancel').addEventListener('click', closeConfirmModal);

    // Toast auto close
    document.getElementById('toastContainer').addEventListener('click', function(e){
        if (e.target.classList.contains('toast')) e.target.remove();
    });
}

function navigateToPage(page) {
    currentPage = page;
    document.querySelectorAll('.nav-item').forEach(item => item.classList.remove('active'));
    document.querySelector(`[data-page="${page}"]`).classList.add('active');
    document.querySelectorAll('.page').forEach(pageEl => pageEl.classList.remove('active'));

    document.getElementById(page + 'Page').classList.add('active');

    // Load data khi chuyển trang
    if (page === 'dashboard') updateDashboard();
    if (page === 'diary') {
        updateDiaryClassStudents();
        renderDiaryPage();
    }
    if (page === 'statistics') updateStatistics();
    if (page === 'students') renderStudentList();
    closeSidebar();
}

// Loading & Toast
function showLoading(show) {
    document.getElementById('loading').style.display = show ? 'flex' : 'none';
}
function showToast(msg, type="info") {
    let icons = {success:'fa-check-circle', error:'fa-times-circle', warning:'fa-exclamation-circle', info:'fa-info-circle'};
    let toast = document.createElement('div');
    toast.className = `toast ${type}`;
    toast.innerHTML = `<i class="fa ${icons[type]||icons.info} toast-icon"></i> ${msg}`;
    document.getElementById('toastContainer').appendChild(toast);
    setTimeout(()=>toast.remove(), 4200);
}

// Sidebar
function toggleSidebar() {
    document.getElementById('sidebar').classList.toggle('active');
    document.getElementById('overlay').classList.toggle('active');
}
function closeSidebar() {
    document.getElementById('sidebar').classList.remove('active');
    document.getElementById('overlay').classList.remove('active');
}

// Date utilities & select
function updateCurrentDate() {
    const d = new Date();
    const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
    document.getElementById('currentDate').textContent = d.toLocaleDateString('vi-VN', options);
}
function populateMonthYearSelects() {
    const monthNames = ['Tháng 1','Tháng 2','Tháng 3','Tháng 4','Tháng 5','Tháng 6','Tháng 7','Tháng 8','Tháng 9','Tháng 10','Tháng 11','Tháng 12'];
    let years = [];
    let y = (new Date()).getFullYear();
    for (let i = -1; i <= 1; i++) years.push(y+i);

    ['dashboardMonth','statsMonth'].forEach(id=>{
        let sel = document.getElementById(id);
        sel.innerHTML = monthNames.map((m,i)=>`<option value="${i+1}">${m}</option>`).join('');
        sel.value = (new Date()).getMonth()+1;
    });
    ['dashboardYear','statsYear'].forEach(id=>{
        let sel = document.getElementById(id);
        sel.innerHTML = years.map(y=>`<option value="${y}">${y}</option>`).join('');
        sel.value = (new Date()).getFullYear();
    });
}
function reloadPage() {
    loadAllData();
    updateAllClassFilters();
    updateDashboard();
    updateDiaryClassStudents();
    updateStatistics();
    renderStudentList();
    showToast('Đã làm mới dữ liệu', 'success');
}

// Data I/O
function loadAllData() {
    students = JSON.parse(localStorage.getItem('students') || '[]');
    diaryData = JSON.parse(localStorage.getItem('diaryData') || '{}');
    disciplineData = JSON.parse(localStorage.getItem('disciplineData') || '{}');
}
function saveAllData() {
    localStorage.setItem('students', JSON.stringify(students));
    localStorage.setItem('diaryData', JSON.stringify(diaryData));
    localStorage.setItem('disciplineData', JSON.stringify(disciplineData));
}
function generateDemoData() {
    students = [
        {id:'S001', code:'S001', name:'Nguyễn Văn An', class:'6A', dob:'2012-10-15'},
        {id:'S002', code:'S002', name:'Trần Thị Bình', class:'6A', dob:'2012-08-21'},
        {id:'S003', code:'S003', name:'Lê Thảo Vy', class:'6B', dob:'2012-12-02'},
        {id:'S004', code:'S004', name:'Phạm Minh Quân', class:'6B', dob:'2012-11-05'}
    ];
    diaryData = {
        "S001": [
            {date:'2025-08-01', subject:'Toán', score:9, note:'Tiến bộ tốt'},
            {date:'2025-08-02', subject:'Văn', score:8, note:'Chăm chỉ'},
        ],
        "S002": [
            {date:'2025-08-01', subject:'Toán', score:6, note:'Cần cố gắng'},
        ],
        "S003": [
            {date:'2025-08-01', subject:'Anh', score:10, note:'Xuất sắc'},
        ]
    };
    disciplineData = {
        "S001": [
            {date:'2025-08-01', type:'Đúng giờ', note:''},
            {date:'2025-08-02', type:'Đi muộn', note:'Do mưa'},
        ],
        "S002": [
            {date:'2025-08-01', type:'Đúng giờ', note:''},
        ]
    };
    saveAllData();
}

// ===== DASHBOARD PAGE =====
function updateDashboard() {
    let classFilter = document.getElementById('dashboardClassFilter').value;
    let month = parseInt(document.getElementById('dashboardMonth').value);
    let year = parseInt(document.getElementById('dashboardYear').value);

    let filtered = students.filter(s => !classFilter || s.class === classFilter);

    // Tổng số học sinh
    let total = filtered.length;
    // Tổng số nhật ký học tập
    let diaryCount = filtered.reduce((sum, s) => sum + ((diaryData[s.id]||[]).filter(r => isInMonthYear(r.date,month,year)).length),0);
    // Tổng số ghi chú nề nếp (vi phạm, đi muộn...)
    let disciplineCount = filtered.reduce((sum,s) => sum+((disciplineData[s.id]||[]).filter(r=>isInMonthYear(r.date,month,year) && r.type!=='Đúng giờ').length),0);
    // Top học sinh (có điểm trung bình >=8 trong tháng)
    let topStudents = filtered.filter(s=>{
        let scores = (diaryData[s.id]||[]).filter(r=>isInMonthYear(r.date,month,year)).map(r=>r.score).filter(x=>typeof x==='number');
        let avg = scores.length? scores.reduce((a,b)=>a+b,0)/scores.length : 0;
        return avg>=8;
    });

    // Render statistic cards
    let html = `
    <div class="stat-card">
        <div class="stat-icon total"><i class="fas fa-users"></i></div>
        <div class="stat-info">
            <h3>${total}</h3><p>Tổng số học sinh</p>
        </div>
    </div>
    <div class="stat-card">
        <div class="stat-icon present"><i class="fas fa-star"></i></div>
        <div class="stat-info">
            <h3>${diaryCount}</h3><p>Lượt ghi nhận học tập</p>
        </div>
    </div>
    <div class="stat-card">
        <div class="stat-icon absent"><i class="fas fa-user-times"></i></div>
        <div class="stat-info">
            <h3>${disciplineCount}</h3><p>Lượt vi phạm/nề nếp</p>
        </div>
    </div>
    <div class="stat-card">
        <div class="stat-icon present"><i class="fas fa-trophy"></i></div>
        <div class="stat-info">
            <h3>${topStudents.length}</h3><p>HS tiêu biểu (>=8đ)</p>
        </div>
    </div>`;
    document.getElementById('overviewStats').innerHTML = html;

    // Top học sinh tiêu biểu
    let content = '';
    if(topStudents.length){
        content += `<h4>Top học sinh tiêu biểu:</h4><ul>`;
        topStudents.forEach(s=>{
            let scores = (diaryData[s.id]||[]).filter(r=>isInMonthYear(r.date,month,year)).map(r=>r.score);
            let avg = scores.length? (scores.reduce((a,b)=>a+b,0)/scores.length).toFixed(1) : '-';
            content += `<li><b>${s.name}</b> (${s.class}) - ĐTB: ${avg}</li>`;
        });
        content += '</ul>';
    } else {
        content = `<div class="empty-state"><i class="fas fa-info-circle"></i><h3>Chưa có học sinh tiêu biểu</h3></div>`;
    }
    document.getElementById('dashboardContent').innerHTML = content;
}

// ===== DIARY PAGE =====
function updateDiaryClassStudents() {
    let classVal = document.getElementById('diaryClassFilter').value;
    let filtered = students.filter(s => !classVal || s.class===classVal);
    let sel = document.getElementById('diaryStudentSelect');
    sel.innerHTML = '<option value="">Chọn học sinh...</option>' + 
        filtered.map(s=>`<option value="${s.id}">${s.name} (${s.class})</option>`).join('');
    if (!filtered.find(s=>s.id===selectedStudentId)) {
        selectedStudentId = filtered[0]?.id || null;
        sel.value = selectedStudentId || '';
    }
}
function renderDiaryPage() {
    let container = document.getElementById('diaryContent');
    if (!selectedStudentId) {
        container.innerHTML = `<div class="empty-state"><i class="fas fa-user-graduate"></i><h3>Chọn học sinh để xem chi tiết</h3></div>`;
        return;
    }
    let s = students.find(s=>s.id===selectedStudentId);
    if (!s) return;

    // Thông tin HS
    let info = `<div style="display:flex;gap:2rem;align-items:center;margin-bottom:2rem;">
        <div style="background:var(--primary-light);width:60px;height:60px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:2rem;color:var(--white);">${getInitials(s.name)}</div>
        <div>
            <h3 style="margin-bottom:0.3rem;">${s.name} <span style="color:var(--gray-500);font-size:0.98rem;">(${s.class})</span></h3>
            <div>Mã HS: <b>${s.code}</b> | Ngày sinh: <b>${formatDate(s.dob)}</b></div>
        </div>
    </div>`;

    // Bảng điểm học tập
    let diaries = (diaryData[s.id]||[]).sort((a,b)=>a.date.localeCompare(b.date));
    let diaryTable = `<h4>Kết quả học tập</h4>
        <table class="student-table" style="margin-bottom:1.2rem;">
            <thead><tr><th>Ngày</th><th>Môn</th><th>Điểm</th><th>Nhận xét</th></tr></thead>
            <tbody>
                ${diaries.map(r=>`<tr><td>${formatDate(r.date)}</td><td>${r.subject}</td><td>${r.score??'-'}</td><td>${r.note??''}</td></tr>`).join('')}
            </tbody>
        </table>
        <div style="margin-bottom:1.5rem;"><button class="btn btn-outline btn-sm" onclick="addDiaryEntry('${s.id}')"><i class="fas fa-plus"></i> Thêm ghi nhận học tập</button></div>
    `;

    // Bảng nề nếp/kỷ luật
    let discs = (disciplineData[s.id]||[]).sort((a,b)=>a.date.localeCompare(b.date));
    let discTable = `<h4>Nề nếp / Kỷ luật</h4>
        <table class="student-table">
            <thead><tr><th>Ngày</th><th>Loại</th><th>Ghi chú</th></tr></thead>
            <tbody>
                ${discs.map(r=>`<tr><td>${formatDate(r.date)}</td><td>${r.type}</td><td>${r.note??''}</td></tr>`).join('')}
            </tbody>
        </table>
        <div style="margin-bottom:1.5rem;"><button class="btn btn-outline btn-sm" onclick="addDisciplineEntry('${s.id}')"><i class="fas fa-plus"></i> Thêm ghi nhận nề nếp</button></div>
    `;

    container.innerHTML = info + diaryTable + discTable;
}
window.addDiaryEntry = function(studentId) {
    openPromptModal('Thêm ghi nhận học tập', [
        {label:'Ngày',type:'date',id:'dDate',required:true, value:today()},
        {label:'Môn học',type:'text',id:'dSubject',required:true},
        {label:'Điểm',type:'number',id:'dScore',required:true, min:0, max:10},
        {label:'Nhận xét',type:'text',id:'dNote',required:false}
    ], (vals)=>{
        diaryData[studentId]=diaryData[studentId]||[];
        diaryData[studentId].push({date:vals.dDate, subject:vals.dSubject, score:Number(vals.dScore), note:vals.dNote});
        saveAllData();
        renderDiaryPage();
        showToast('Đã thêm ghi nhận học tập','success');
    });
}
window.addDisciplineEntry = function(studentId) {
    openPromptModal('Thêm ghi nhận nề nếp', [
        {label:'Ngày',type:'date',id:'kDate',required:true, value:today()},
        {label:'Loại',type:'select',id:'kType',required:true, options:['Đúng giờ','Đi muộn','Nghỉ phép','Vi phạm','Khen thưởng']},
        {label:'Ghi chú',type:'text',id:'kNote',required:false}
    ], (vals)=>{
        disciplineData[studentId]=disciplineData[studentId]||[];
        disciplineData[studentId].push({date:vals.kDate, type:vals.kType, note:vals.kNote});
        saveAllData();
        renderDiaryPage();
        showToast('Đã thêm ghi nhận nề nếp','success');
    });
}

// ===== STATISTICS PAGE =====
function updateStatistics() {
    let classVal = document.getElementById('statsClass').value;
    let month = parseInt(document.getElementById('statsMonth').value);
    let year = parseInt(document.getElementById('statsYear').value);

    let filtered = students.filter(s => !classVal || s.class === classVal);

    // Thống kê trung bình điểm học tập, số lượt vi phạm, % chuyên cần...
    let statTable = `
    <table class="student-table">
        <thead>
            <tr>
                <th>Học sinh</th>
                <th>Lớp</th>
                <th>ĐTB</th>
                <th>Số lượt học tập</th>
                <th>Vi phạm/nề nếp</th>
                <th>Khen thưởng</th>
            </tr>
        </thead>
        <tbody>
    `;
    for (let s of filtered) {
        let diaries = (diaryData[s.id]||[]).filter(r=>isInMonthYear(r.date,month,year));
        let avg = diaries.length? (diaries.map(x=>x.score).reduce((a,b)=>a+b,0)/diaries.length).toFixed(2) : '-';
        let dis = (disciplineData[s.id]||[]).filter(r=>isInMonthYear(r.date,month,year));
        let viPham = dis.filter(x=>x.type==='Vi phạm').length;
        let khenThuong = dis.filter(x=>x.type==='Khen thưởng').length;

        statTable += `<tr>
            <td>${s.name}</td>
            <td>${s.class}</td>
            <td>${avg}</td>
            <td>${diaries.length}</td>
            <td>${viPham}</td>
            <td>${khenThuong}</td>
        </tr>`;
    }
    statTable += '</tbody></table>';
    document.getElementById('statisticsContent').innerHTML = statTable;
}

// ===== STUDENT MANAGEMENT PAGE =====
function renderStudentList() {
    let keyword = (document.getElementById('studentSearch').value||'').toLowerCase();
    let filtered = students.filter(s=>!keyword || (s.name + s.class + s.code).toLowerCase().includes(keyword));
    let tbody = document.getElementById('studentTableBody');
    tbody.innerHTML = filtered.map(s=>
        `<tr>
            <td>${s.code}</td>
            <td>${s.name}</td>
            <td>${s.class}</td>
            <td>${formatDate(s.dob)}</td>
            <td class="actions">
                <button class="btn btn-outline btn-sm" onclick="openEditStudentModal('${s.id}')"><i class="fas fa-pen"></i> Sửa</button>
                <button class="btn btn-danger btn-sm" onclick="deleteStudent('${s.id}')"><i class="fas fa-trash"></i> Xóa</button>
            </td>
        </tr>`
    ).join('');
}
function openAddStudentModal() {
    isEditingStudent = false;
    editingStudentId = null;
    openStudentModal();
}
function openEditStudentModal(id) {
    isEditingStudent = true;
    editingStudentId = id;
    openStudentModal(students.find(s=>s.id===id));
}
function openStudentModal(data={}) {
    document.getElementById('modalTitle').textContent = isEditingStudent?'Sửa Học Sinh':'Thêm Học Sinh';
    document.getElementById('studentCode').value = data.code||'';
    document.getElementById('studentName').value = data.name||'';
    document.getElementById('studentClass').value = data.class||'';
    document.getElementById('studentDOB').value = data.dob||'';
    document.getElementById('studentModal').classList.add('active');
}
function closeStudentModal() {
    document.getElementById('studentModal').classList.remove('active');
}
function saveStudent(e) {
    e?.preventDefault();
    let code = document.getElementById('studentCode').value.trim();
    let name = document.getElementById('studentName').value.trim();
    let cls = document.getElementById('studentClass').value.trim();
    let dob = document.getElementById('studentDOB').value;

    if (!name || !cls || !dob) {
        showToast('Vui lòng nhập đủ thông tin', 'warning'); return;
    }
    if (!code) code = randomId();
    if (isEditingStudent) {
        let idx = students.findIndex(s=>s.id===editingStudentId);
        if(idx>=0){
            students[idx] = {id:editingStudentId, code, name, class:cls, dob};
            showToast('Cập nhật học sinh thành công','success');
        }
    } else {
        let id = randomId();
        students.push({id, code, name, class:cls, dob});
        showToast('Thêm học sinh thành công','success');
    }
    saveAllData();
    renderStudentList();
    closeStudentModal();
    updateAllClassFilters();
}
function deleteStudent(id) {
    let s = students.find(s=>s.id===id);
    if (!s) return;
    openConfirmModal(`Bạn chắc chắn muốn xóa học sinh <b>${s.name}</b>?`, ()=>{
        students = students.filter(x=>x.id!==id);
        delete diaryData[id];
        delete disciplineData[id];
        saveAllData();
        renderStudentList();
        showToast('Đã xóa học sinh','success');
        updateAllClassFilters();
    });
}
function searchStudents() { renderStudentList(); }

// ===== Modal Confirm & Prompt =====
function openConfirmModal(msg, onOk) {
    document.getElementById('confirmMessage').innerHTML = msg;
    document.getElementById('confirmModal').classList.add('active');
    document.getElementById('confirmOk').onclick = ()=>{
        closeConfirmModal(); if(onOk) onOk();
    };
}
function closeConfirmModal() {
    document.getElementById('confirmModal').classList.remove('active');
}
function openPromptModal(title, fields, onSubmit) {
    let modal = document.createElement('div');
    modal.className = 'modal active';
    let formHtml = `<div class="modal-content"><div class="modal-header"><h3>${title}</h3>
        <button class="modal-close" onclick="this.closest('.modal').remove()"><i class="fas fa-times"></i></button></div>
        <form class="modal-body" id="promptForm">`;

    fields.forEach(f=>{
        formHtml += `<div class="form-group"><label>${f.label}${f.required?' *':''}</label>`;
        if(f.type==='select') {
            formHtml += `<select id="${f.id}" class="form-select">${f.options.map(opt=>`<option value="${opt}">${opt}</option>`).join('')}</select>`;
        } else {
            formHtml += `<input id="${f.id}" class="form-input" type="${f.type}" ${f.required?'required':''} ${f.min?'min="'+f.min+'"':''} ${f.max?'max="'+f.max+'"':''} value="${f.value||''}"/>`;
        }
        formHtml += '</div>';
    });
    formHtml += `</form>
        <div class="modal-footer">
            <button class="btn btn-outline" onclick="this.closest('.modal').remove()">Hủy</button>
            <button class="btn btn-primary" type="submit" form="promptForm">Lưu</button>
        </div>
    </div>`;
    modal.innerHTML = formHtml;
    document.body.appendChild(modal);

    document.getElementById('promptForm').onsubmit = function(e){
        e.preventDefault();
        let vals = {};
        fields.forEach(f=>{
            let el = document.getElementById(f.id);
            vals[f.id] = el.value;
        });
        modal.remove();
        onSubmit(vals);
    };
}

// ===== Utilities & Support =====
function today() {
    let d = new Date();
    return d.toISOString().slice(0,10);
}
function getInitials(name) {
    return name.split(' ').map(x=>x[0]).join('').toUpperCase().slice(0,2);
}
function formatDate(str) {
    if (!str) return '-';
    let d = new Date(str);
    return `${d.getDate().toString().padStart(2,'0')}/${(d.getMonth()+1).toString().padStart(2,'0')}/${d.getFullYear()}`;
}
function randomId() {
    return 'S' + Math.random().toString(36).substr(2,4).toUpperCase() + Date.now().toString().slice(-3);
}
function isInMonthYear(dateStr, month, year) {
    let d = new Date(dateStr);
    return d.getMonth()+1 === month && d.getFullYear() === year;
}
function showMainApp() {
    // Ẩn/hiện nút logout (demo user)
    document.getElementById('logoutBtn').style.display = 'flex';
    document.getElementById('currentUser').textContent = currentUser.name;
    // Mặc định trang dashboard
    navigateToPage('dashboard');
}

// Tự động update class filter các select
function updateAllClassFilters() {
    let classList = Array.from(new Set(students.map(s=>s.class))).sort();
    let opts = '<option value="">Tất cả lớp</option>' + classList.map(c=>`<option value="${c}">${c}</option>`).join('');
    ['dashboardClassFilter','diaryClassFilter','statsClass'].forEach(id=>{
        let el = document.getElementById(id);
        if (el) { el.innerHTML = opts; }
    });
}

// ==== End JS ====
</script>
