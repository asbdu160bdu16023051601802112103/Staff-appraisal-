<html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Bon Secours College Staff Appraisal System</title>

<!-- SheetJS for Excel export -->
<script src="https://cdn.sheetjs.com/xlsx-latest/package/dist/xlsx.full.min.js"></script>

<style>
  body { 
    font-family: Arial, sans-serif; 
    background: #f5f7fb; 
    padding: 18px; 
    color: #222; 
    margin: 0;
  }
  
  /* College Header */
  .college-header {
    background: linear-gradient(135deg, #0b486b 0%, #1c6ea4 100%);
    color: white;
    padding: 15px 20px;
    border-radius: 8px;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 4px 12px rgba(20,20,50,0.15);
  }
  
  .college-logo-container {
    display: flex;
    align-items: center;
    gap: 20px;
  }
  
  .college-logo {
    height: 80px;
    width: auto;
    max-width: 120px;
    object-fit: contain;
    border-radius: 8px;
    background: white;
    padding: 5px;
  }
  
  .college-name {
    flex-grow: 1;
  }
  
  .college-name h1 {
    margin: 0;
    font-size: 24px;
    color: white;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }
  
  .college-name h2 {
    margin: 5px 0 0 0;
    font-size: 16px;
    font-weight: normal;
    color: rgba(255,255,255,0.9);
    font-style: italic;
  }
  
  .system-title {
    background: rgba(255,255,255,0.1);
    padding: 10px 15px;
    border-radius: 6px;
    border-left: 4px solid #28a745;
  }
  
  .system-title h3 {
    margin: 0;
    font-size: 18px;
    color: white;
  }
  
  .card { 
    background: #fff; 
    border-radius: 8px; 
    padding: 20px; 
    margin: 12px auto; 
    width: 100%; 
    max-width: 1000px; 
    box-shadow: 0 6px 18px rgba(20,20,50,0.08); 
    border-top: 5px solid #0b486b;
  }
  
  h1 { 
    margin: 0 0 12px 0; 
    font-size: 20px; 
    color: #0b486b;
  }
  
  h2 { 
    color: #0b486b; 
    margin: 20px 0 10px 0; 
    font-size: 18px; 
    border-bottom: 2px solid #f0f0f0;
    padding-bottom: 5px;
  }
  
  .section { 
    border: 1px solid #e0e5ec; 
    padding: 15px; 
    margin: 12px 0; 
    border-radius: 6px; 
    background: #fcfeff;
    transition: all 0.3s ease;
  }
  
  .section:hover {
    box-shadow: 0 3px 10px rgba(0,119,204,0.1);
    border-color: #c0d6e4;
  }
  
  .row { 
    display: flex; 
    gap: 15px; 
    flex-wrap: wrap; 
    margin-bottom: 10px;
  }
  
  label { 
    display: block; 
    font-size: 13px; 
    margin-bottom: 6px; 
    font-weight: 600;
    color: #444;
  }
  
  input[type="text"], input[type="number"], textarea, select { 
    width: 100%; 
    padding: 10px; 
    border-radius: 6px; 
    border: 1px solid #d7dbe0; 
    font-size: 14px;
    transition: border 0.3s;
  }
  
  input[type="text"]:focus, input[type="number"]:focus, textarea:focus, select:focus { 
    border-color: #0077cc;
    outline: none;
    box-shadow: 0 0 0 3px rgba(0,119,204,0.1);
  }
  
  input[type="file"] { 
    padding: 8px 4px; 
    border: 1px dashed #ccc;
    border-radius: 6px;
    background: #f9f9f9;
  }
  
  .col { 
    flex: 1 1 220px; 
    min-width: 180px; 
  }
  
  .small { 
    flex: 0 0 120px; 
  }
  
  .actions { 
    margin-top: 20px; 
    display: flex; 
    gap: 10px; 
    align-items: center; 
    flex-wrap: wrap; 
    padding-top: 15px;
    border-top: 1px solid #eee;
  }
  
  button { 
    background: #0077cc; 
    color: #fff; 
    padding: 10px 16px; 
    border: none; 
    border-radius: 6px; 
    cursor: pointer;
    font-weight: 600;
    font-size: 14px;
    transition: all 0.3s;
    display: inline-flex;
    align-items: center;
    gap: 5px;
  }
  
  button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,119,204,0.3);
  }
  
  button.secondary { 
    background: #5f6b77; 
  }
  
  button.secondary:hover {
    background: #4a555f;
    box-shadow: 0 4px 8px rgba(95,107,119,0.3);
  }
  
  button.admin { 
    background: #28a745; 
  }
  
  button.admin:hover {
    background: #218838;
    box-shadow: 0 4px 8px rgba(40,167,69,0.3);
  }
  
  button.danger { 
    background: #dc3545; 
  }
  
  button.danger:hover {
    background: #c82333;
    box-shadow: 0 4px 8px rgba(220,53,69,0.3);
  }
  
  button.warning { 
    background: #ffc107; 
    color: #212529; 
  }
  
  button.warning:hover {
    background: #e0a800;
    box-shadow: 0 4px 8px rgba(255,193,7,0.3);
  }
  
  .result { 
    background: #fffef6; 
    border-left: 6px solid #f2b705; 
    padding: 15px; 
    margin-top: 15px; 
    border-radius: 6px; 
    box-shadow: 0 3px 10px rgba(0,0,0,0.05);
  }
  
  table { 
    border-collapse: collapse; 
    width: 100%; 
    margin-top: 10px; 
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
  }
  
  td, th { 
    padding: 10px; 
    border: 1px solid #e0e5ec; 
    font-size: 13px; 
  }
  
  th {
    background: #f8f9fa;
    font-weight: 600;
    color: #0b486b;
  }
  
  .score { 
    font-weight: 700; 
    color: #0077cc; 
    font-size: 14px;
  }
  
  .proof-note { 
    font-size: 12px; 
    color: #666; 
    font-style: italic;
    margin-top: 5px;
  }
  
  .section-title { 
    font-weight: 700; 
    color: #0b486b; 
    margin-bottom: 12px; 
    font-size: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  
  .section-title:before {
    content: "📋";
    font-size: 18px;
  }
  
  .admin-panel { 
    background: #f8f9fa; 
    border: 2px solid #28a745; 
    margin-top: 20px; 
    padding: 20px; 
    border-radius: 8px; 
  }
  
  .hidden { 
    display: none; 
  }
  
  .login-form { 
    max-width: 400px; 
    margin: 40px auto; 
    padding: 30px; 
    background: white; 
    border-radius: 8px; 
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
    border-top: 5px solid #0b486b;
  }
  
  .login-form input { 
    margin-bottom: 15px; 
  }
  
  .mode-switch { 
    text-align: right; 
    margin-bottom: 15px; 
  }
  
  .status-message { 
    padding: 12px 15px; 
    margin: 15px 0; 
    border-radius: 6px; 
    font-size: 14px;
  }
  
  .success { 
    background: #d4edda; 
    color: #155724; 
    border: 1px solid #c3e6cb; 
  }
  
  .error { 
    background: #f8d7da; 
    color: #721c24; 
    border: 1px solid #f5c6cb; 
  }
  
  .warning { 
    background: #fff3cd; 
    color: #856404; 
    border: 1px solid #ffeaa7; 
  }
  
  .info { 
    background: #d1ecf1; 
    color: #0c5460; 
    border: 1px solid #bee5eb; 
  }
  
  .data-table { 
    margin-top: 20px; 
    font-size: 13px; 
  }
  
  .data-table th { 
    background: #f8f9fa; 
  }
  
  .highlight { 
    background: #fff3cd; 
  }
  
  .footer {
    text-align: center;
    margin-top: 30px;
    padding: 15px;
    color: #666;
    font-size: 12px;
    border-top: 1px solid #eee;
  }
  
  .total-score-display {
    background: linear-gradient(135deg, #0b486b 0%, #1c6ea4 100%);
    color: white;
    padding: 10px 20px;
    border-radius: 6px;
    font-size: 18px;
    font-weight: bold;
    display: inline-block;
    margin-left: auto;
  }
  
  .remarks-section {
    background: #f8f9fa;
    padding: 15px;
    border-radius: 6px;
    margin-top: 10px;
    border: 1px solid #e0e5ec;
  }
  
  .remarks-section textarea {
    width: 100%;
    padding: 10px;
    border-radius: 6px;
    border: 1px solid #d7dbe0;
    font-size: 14px;
    margin-top: 5px;
  }
  
  @media (max-width: 768px) {
    .college-header {
      flex-direction: column;
      text-align: center;
      gap: 15px;
    }
    
    .college-logo-container {
      flex-direction: column;
      gap: 10px;
    }
    
    .system-title {
      width: 100%;
    }
    
    .row {
      gap: 10px;
    }
    
    .col {
      flex: 1 1 100%;
    }
    
    .actions {
      flex-direction: column;
      align-items: stretch;
    }
    
    button {
      width: 100%;
      justify-content: center;
    }
    
    .total-score-display {
      width: 100%;
      text-align: center;
      margin: 10px 0;
    }
  }
</style>
</head>
<body>

<!-- College Header with Logo -->
<div class="college-header">
  <div class="college-logo-container">
    <img src="data:image/jpeg;base64,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" alt="Bon Secours College for Women Logo" class="college-logo">
    <div class="college-name">
      <h1>BON SECOURS COLLEGE FOR WOMEN (AUTONOMOUS)</h1>
      <h2>Empowering Women through Quality Education</h2>
    </div>
  </div>
  <div class="system-title">
    <h3>Staff Appraisal System</h3>
  </div>
</div>

<!-- Login Form (for Admin) -->
<div id="loginForm" class="login-form hidden">
  <div style="text-align: center; margin-bottom: 20px;">
    <img src="data:image/jpeg;base64,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" alt="Bon Secours College for Women Logo" class="college-logo" alt="Bon Secours College Logo" style="height: 60px; width: auto; margin: 0 auto; display: block; border-radius: 6px; background: white; padding: 5px;">
    <h2 style="color: #0b486b; margin-top: 10px;">Admin Login</h2>
    <p style="color: #666; font-size: 14px;">Bon Secours College Staff Appraisal System</p>
  </div>
  <input type="password" id="adminPassword" placeholder="Enter Admin Password" style="width:100%; padding:12px; margin-bottom:20px; border-radius:6px; border:1px solid #ddd;">
  <button onclick="loginAsAdmin()" style="width:100%; padding:12px; background:#28a745; color:white; border:none; border-radius:6px; font-size:16px;">Login as Admin</button>
  <div style="text-align:center; margin-top:20px;">
    <button onclick="switchToStaffMode()" class="secondary" style="padding:10px 20px;">Staff Mode</button>
  </div>
</div>

<!-- Main Appraisal Form -->
<div id="appraisalForm" class="card">
  <div class="mode-switch">
    <button id="switchModeBtn" onclick="switchToAdminMode()" class="admin">🔒 Admin Mode</button>
  </div>
  
  <h1>📊 Staff Appraisal System - Complete 28 Sections</h1>
  <p style="margin:0 0 15px 0; color:#444; background:#f8f9fa; padding:10px; border-radius:6px; border-left:4px solid #0b486b;">
    Fill all 28 sections. Upload proof files where required for scoring. <strong>Total Score: 200 points.</strong>
  </p>

  <!-- Status Message -->
  <div id="statusMessage" class="status-message hidden"></div>

  <!-- Personal Info -->
  <div class="section">
    <div class="section-title">👤 1. Personal Information</div>
    <div class="row">
      <div class="col">
        <label>Staff Name *</label>
        <input id="staff_name" type="text" placeholder="Full Name" required>
      </div>
      <div class="col">
        <label>Department *</label>
        <input id="dept" type="text" placeholder="Department" required>
      </div>
      <div class="col">
        <label>Designation *</label>
        <input id="designation" type="text" placeholder="Designation" required>
      </div>
      <div class="small">
        <label>Academic Year *</label>
        <input id="acyear" type="text" placeholder="2024-2025" required>
      </div>
    </div>
    <div class="row" style="margin-top:10px;">
      <div class="col">
        <label>Email ID</label>
        <input id="email" type="text" placeholder="email@bonsecourscollege.edu">
      </div>
      <div class="col">
        <label>Employee ID</label>
        <input id="emp_id" type="text" placeholder="EMP001">
      </div>
    </div>
  </div>

  <!-- SECTION 1: Leave / Permission / On Duty -->
  <div class="section">
    <div class="section-title">📅 2. Leave / Permission / On Duty</div>
    <div class="row">
      <div class="col">
        <label>Casual Leave days taken</label>
        <input id="cl_days" type="number" min="0" max="365" value="0">
      </div>
      <div class="col">
        <label>Loss of Pay days</label>
        <input id="lop_days" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Permission Hours</label>
        <input id="perm_count" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>On Duty days</label>
        <input id="onduty_days" type="number" min="0" value="0">
        <label class="proof-note">Proof (upload):</label>
        <input id="onduty_proof" type="file" accept=".pdf,.jpg,.jpeg,.png">
      </div>
    </div>
  </div>

  <!-- SECTION 2: Professional Development -->
  <div class="section">
    <div class="section-title">🎓 3. Professional Development</div>
    
    <div class="row">
      <div class="col">
        <label>Qualification Upgradation</label>
        <select id="qual_upg">
          <option value="0">No</option>
          <option value="5">Yes (5 points)</option>
        </select>
        <label class="proof-note">Proof:</label>
        <input id="qual_proof" type="file" accept=".pdf,.jpg,.jpeg,.png">
      </div>
      <div class="col">
        <label>FDP days attended</label>
        <input id="fdp_days" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="fdp_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
    
    <div class="row" style="margin-top:10px;">
      <div class="col">
        <label>Seminars/Workshops Attended</label>
        <input id="seminar_att" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="seminar_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
      <div class="col">
        <label>Seminars/Workshops Organized</label>
        <input id="seminar_org" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="seminar_org_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 3: Online Courses & e-Content -->
  <div class="section">
    <div class="section-title">💻 4. Online Courses & e-Content</div>
    <div class="row">
      <div class="col">
        <label>Online courses completed</label>
        <input id="online_courses" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="online_proof" type="file" accept=".pdf,.jpg,.png" multiple>
      </div>
      <div class="col">
        <label>e-Contents developed</label>
        <input id="econtent_count" type="number" min="0" value="0">
      </div>
    </div>
  </div>

  <!-- SECTION 4: Awards & Recognitions -->
  <div class="section">
    <div class="section-title">🏆 5. Awards & Recognitions</div>
    <div class="row">
      <div class="col">
        <label>Number of awards</label>
        <input id="awards_count" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="awards_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 5: Memberships -->
  <div class="section">
    <div class="section-title">🤝 6. Memberships in Academic Bodies</div>
    <div class="row">
      <div class="col">
        <label>Active memberships</label>
        <input id="memberships" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="memberships_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 6: Administrative Actions -->
  <div class="section">
    <div class="section-title">⚖️ 7. Administrative Actions</div>
    <div class="row">
      <div class="col">
        <label>Administrative penalties?</label>
        <select id="admin_action">
          <option value="0">No</option>
          <option value="-5">Yes (-5 points)</option>
        </select>
      </div>
    </div>
  </div>

  <!-- SECTION 7: Curriculum Development -->
  <div class="section">
    <div class="section-title">📚 8. Curriculum Development</div>
    <div class="row">
      <div class="col">
        <label>Contributions to curriculum</label>
        <input id="curriculum_count" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="curriculum_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 8: Teaching Learning & Evaluation -->
  <div class="section">
    <div class="section-title">👨‍🏫 9. Teaching Learning & Evaluation</div>
    <div class="row">
      <div class="col">
        <label>Workload (hours/week)</label>
        <input id="workload" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Courses taught</label>
        <input id="courses_taught" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Remedial classes</label>
        <input id="remedial" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Exam duties</label>
        <input id="examduties" type="number" min="0" value="0">
      </div>
    </div>
    <div style="margin-top:10px;">
      <label>Course file submitted?</label>
      <select id="coursefile_sub">
        <option value="0">No</option>
        <option value="5">Yes (5 points)</option>
      </select>
      <label class="proof-note">Proof:</label>
      <input id="coursefile_proof" type="file" accept=".pdf,.jpg,.jpeg,.png">
    </div>
  </div>

  <!-- SECTION 9: Value Added Courses -->
  <div class="section">
    <div class="section-title">➕ 10. Value Added Courses</div>
    <div class="row">
      <div class="col">
        <label>Value-added courses offered</label>
        <input id="value_courses" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="value_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 10: Co-curricular Activities -->
  <div class="section">
    <div class="section-title">🎭 11. Co-curricular Activities</div>
    <div class="row">
      <div class="col">
        <label>Activities organized</label>
        <input id="co_curricular" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="co_curricular_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 11: Extra-curricular Activities -->
  <div class="section">
    <div class="section-title">🏀 12. Extra-curricular Activities</div>
    <div class="row">
      <div class="col">
        <label>Activities as advisor</label>
        <input id="extra_activities" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="extra_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 12: Social Responsibility -->
  <div class="section">
    <div class="section-title">🤲 13. Social Responsibility</div>
    <div class="row">
      <div class="col">
        <label>Programs participated</label>
        <input id="social_prog" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="social_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 13: Student Projects -->
  <div class="section">
    <div class="section-title">🔬 14. Student Projects</div>
    <div class="row">
      <div class="col">
        <label>Projects guided</label>
        <input id="projects_guided" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="projects_proof" type="file" accept=".pdf,.docx,.zip" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 14: Internship Guidance -->
  <div class="section">
    <div class="section-title">💼 15. Internship / Training</div>
    <div class="row">
      <div class="col">
        <label>Internships guided</label>
        <input id="internships" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="internships_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 15: Tutor-Ward System -->
  <div class="section">
    <div class="section-title">👥 16. Tutor-Ward System</div>
    <div class="row">
      <div class="col">
        <label>Number of mentees</label>
        <input id="mentees" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="mentees_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 16: Class In-Charge -->
  <div class="section">
    <div class="section-title">👑 17. Class In-Charge</div>
    <div class="row">
      <div class="col">
        <label>Were you class in-charge?</label>
        <select id="incharge">
          <option value="0">No</option>
          <option value="5">Yes (5 points)</option>
        </select>
      </div>
    </div>
  </div>

  <!-- SECTION 17: Student Results -->
  <div class="section">
    <div class="section-title">📊 18. Student Results</div>
    <div class="row">
      <div class="col">
        <label>Average pass % (0-100)</label>
        <input id="pass_percent" type="number" min="0" max="100" value="0">
        <label class="proof-note">Proof:</label>
        <input id="pass_proof" type="file" accept=".pdf,.jpg,.jpeg,.png">
      </div>
    </div>
  </div>

  <!-- SECTION 18: Student Attendance -->
  <div class="section">
    <div class="section-title">📈 19. Student Attendance</div>
    <div class="row">
      <div class="col">
        <label>Attendance % in classes</label>
        <input id="stud_att_percent" type="number" min="0" max="100" value="0">
        <label class="proof-note">Proof:</label>
        <input id="stud_att_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 19: Exam Attendance -->
  <div class="section">
    <div class="section-title">📝 20. Exam Attendance</div>
    <div class="row">
      <div class="col">
        <label>Exam attendance %</label>
        <input id="exam_att_percent" type="number" min="0" max="100" value="0">
        <label class="proof-note">Proof:</label>
        <input id="exam_att_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 20: Parent Meetings -->
  <div class="section">
    <div class="section-title">👨‍👩‍👧‍👦 21. Parent Meetings</div>
    <div class="row">
      <div class="col">
        <label>Parent meetings conducted</label>
        <input id="parent_meet" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="parent_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 21: Slow Learners -->
  <div class="section">
    <div class="section-title">🐢 22. Slow Learners</div>
    <div class="row">
      <div class="col">
        <label>Slow learners assisted</label>
        <input id="slow_learners" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="slow_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 22: Advanced Learners -->
  <div class="section">
    <div class="section-title">🚀 23. Advanced Learners</div>
    <div class="row">
      <div class="col">
        <label>Advanced learners tasks</label>
        <input id="adv_learners" type="number" min="0" value="0">
        <label class="proof-note">Proof:</label>
        <input id="adv_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 23-24: Research -->
  <div class="section">
    <div class="section-title">🔬 24-25. Research Activities</div>
    <div class="row">
      <div class="col">
        <label>Research papers published</label>
        <input id="research_papers" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Research projects</label>
        <input id="research_projects" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label class="proof-note">Proof:</label>
        <input id="research_proof" type="file" accept=".pdf,.docx,.jpg" multiple>
      </div>
    </div>
  </div>

  <!-- SECTION 25-27: Leadership -->
  <div class="section">
    <div class="section-title">🌟 26-28. Leadership & Governance</div>
    <div class="row">
      <div class="col">
        <label>Leadership roles</label>
        <input id="leadership_roles" type="number" min="0" value="0">
      </div>
      <div class="col">
        <label>Files maintained?</label>
        <select id="files_maint">
          <option value="0">No</option>
          <option value="5">Yes (5 points)</option>
        </select>
      </div>
      <div class="col">
        <label class="proof-note">Proof:</label>
        <input id="leadership_proof" type="file" accept=".pdf,.jpg,.jpeg,.png" multiple>
      </div>
    </div>
  </div>

  <!-- Self Assessment -->
  <div class="section">
    <div class="section-title">📝 Self-Assessment & Additional Info</div>
    <div class="row">
      <div class="col">
        <label>Strengths</label>
        <textarea id="strengths" rows="3" placeholder="Your key strengths..."></textarea>
      </div>
      <div class="col">
        <label>Areas for Improvement</label>
        <textarea id="weaknesses" rows="3" placeholder="Areas to improve..."></textarea>
      </div>
    </div>
    <div class="row" style="margin-top:10px;">
      <div class="col">
        <label>Additional Achievements</label>
        <textarea id="achievements" rows="2" placeholder="Any other achievements..."></textarea>
      </div>
      <div class="col">
        <label>Future Goals</label>
        <textarea id="future_goals" rows="2" placeholder="Your future goals..."></textarea>
      </div>
    </div>
  </div>

  <!-- Remarks Section (for Admin/Reviewer) -->
  <div class="section remarks-section">
    <div class="section-title">📝 Remarks & Recommendations</div>
    <div class="row">
      <div class="col">
        <label>Reviewer Remarks</label>
        <textarea id="reviewer_remarks" rows="3" placeholder="Enter remarks from reviewer..."></textarea>
      </div>
      <div class="col">
        <label>HOD Remarks</label>
        <textarea id="hod_remarks" rows="3" placeholder="Enter remarks from HOD..."></textarea>
      </div>
    </div>
    <div class="row" style="margin-top:10px;">
      <div class="col">
        <label>Principal Remarks</label>
        <textarea id="principal_remarks" rows="3" placeholder="Enter remarks from Principal..."></textarea>
      </div>
      <div class="col">
        <label>Overall Recommendations</label>
        <textarea id="recommendations" rows="3" placeholder="Overall recommendations..."></textarea>
      </div>
    </div>
  </div>

  <!-- Actions for Staff Mode -->
  <div class="actions" id="staffActions">
    <button id="calcBtn">📊 Calculate & Download Excel</button>
    <button id="previewBtn" class="secondary">👁️ Preview Score</button>
    <button id="saveToLocalBtn" class="secondary">💾 Save Data</button>
    <button id="viewMyDataBtn" class="secondary">📋 View My Data</button>
    <button id="clearFormBtn" class="warning">🗑️ Clear Form</button>
    <div id="totalDisplay" class="total-score-display"></div>
  </div>

  <!-- Actions for Admin Mode -->
  <div class="actions hidden" id="adminActions">
    <button onclick="viewAllStaffData()" class="admin">👥 View All Staff Data</button>
    <button onclick="exportAllStaffExcel()" class="admin">📈 Export All to Excel</button>
    <button onclick="backupData()" class="admin">💾 Backup Data</button>
    <button onclick="searchStaffData()" class="secondary">🔍 Search Staff</button>
    <button onclick="clearAllData()" class="danger">🗑️ Clear All Data</button>
    <button onclick="switchToStaffMode()" class="secondary">👤 Switch to Staff Mode</button>
  </div>

  <div id="preview" class="result" style="display:none;"></div>

  <!-- Admin Panel -->
  <div id="adminPanel" class="admin-panel hidden">
    <h3 style="color: #28a745; border-bottom: 2px solid #28a745; padding-bottom: 10px;">👑 Admin Panel - All Staff Records</h3>
    <div id="searchBox" style="margin-bottom:15px; display: flex; gap: 10px; align-items: center;">
      <input type="text" id="searchInput" placeholder="Search by name, department..." style="flex-grow:1; padding:10px; border-radius:6px; border:1px solid #ddd;">
      <button onclick="searchStaffData()">🔍 Search</button>
      <button onclick="viewAllStaffData()" class="secondary">📋 Show All</button>
      <button onclick="restoreData()" class="secondary" title="Restore from backup">📥 Restore</button>
    </div>
    <div id="adminDataDisplay"></div>
  </div>
</div>

<!-- Footer -->
<div class="footer">
  <p>© 2024 Bon Secours College for Women - Staff Appraisal System | Version 2.0</p>
  <p>Developed for Academic Excellence and Staff Development</p>
</div>

<script>
// ==================== GLOBAL VARIABLES ====================
const ADMIN_PASSWORD = "admin123";
let isAdminMode = false;
let allStaffData = [];

// Section names mapping for Excel columns
const SECTION_NAMES = {
  section1: 'Leaves/On Duty (Max: 12)',
  section2: 'Professional Development (Max: 20)',
  section3: 'Online Courses (Max: 10)',
  section4: 'Awards (Max: 5)',
  section5: 'Memberships (Max: 5)',
  section6: 'Admin Actions (Max: -5)',
  section7: 'Curriculum Development (Max: 5)',
  section8: 'Teaching Learning & Evaluation (Max: 20)',
  section9: 'Value Added Courses (Max: 5)',
  section10: 'Co-curricular Activities (Max: 5)',
  section11: 'Extra-curricular Activities (Max: 5)',
  section12: 'Social Responsibility (Max: 5)',
  section13: 'Student Projects (Max: 5)',
  section14: 'Internship/Training (Max: 5)',
  section15: 'Tutor-Ward System (Max: 5)',
  section16: 'Class In-charge (Max: 5)',
  section17: 'Student Results (Max: 5)',
  section18: 'Student Attendance (Max: 5)',
  section19: 'Exam Attendance (Max: 5)',
  section20: 'Parent Meetings (Max: 5)',
  section21: 'Slow Learners (Max: 5)',
  section22: 'Advanced Learners (Max: 5)',
  section23_24: 'Research Activities (Max: 15)',
  section25_27: 'Leadership & Governance (Max: 15)'
};

// ==================== HELPER FUNCTIONS ====================
function showMessage(message, type = 'info') {
  const msgDiv = document.getElementById('statusMessage');
  msgDiv.innerHTML = message;
  msgDiv.className = `status-message ${type}`;
  msgDiv.classList.remove('hidden');
  setTimeout(() => {
    msgDiv.classList.add('hidden');
  }, 5000);
}

function isLocalStorageAvailable() {
  try {
    localStorage.setItem('test', 'test');
    localStorage.removeItem('test');
    return true;
  } catch(e) {
    return false;
  }
}

function hasFiles(id) {
  const el = document.getElementById(id);
  return el && el.files && el.files.length > 0;
}

// ==================== DATA STORAGE FUNCTIONS ====================
function loadAllStaffData() {
  if (!isLocalStorageAvailable()) {
    showMessage("LocalStorage not available. Data cannot be saved.", 'error');
    return [];
  }
  
  const data = localStorage.getItem('staffAppraisalData');
  if (!data) return [];
  
  try {
    allStaffData = JSON.parse(data);
    return allStaffData;
  } catch(e) {
    console.error("Error parsing data:", e);
    showMessage("Error loading saved data.", 'error');
    return [];
  }
}

function saveAllStaffData() {
  if (!isLocalStorageAvailable()) {
    showMessage("LocalStorage not available.", 'error');
    return false;
  }
  
  try {
    localStorage.setItem('staffAppraisalData', JSON.stringify(allStaffData));
    return true;
  } catch(e) {
    console.error("Error saving all data:", e);
    showMessage("Error saving data: " + e.message, 'error');
    return false;
  }
}

function saveStaffData(staffData) {
  if (!isLocalStorageAvailable()) {
    showMessage("LocalStorage not available.", 'error');
    return false;
  }
  
  try {
    // Validate required fields
    if (!staffData.StaffName || !staffData.AcademicYear) {
      showMessage("Please fill in required fields (Name and Academic Year).", 'error');
      return false;
    }
    
    // Load existing data
    allStaffData = loadAllStaffData();
    
    // Generate unique ID
    staffData.id = staffData.id || Date.now().toString() + Math.random().toString(36).substr(2, 9);
    staffData.SaveDate = new Date().toLocaleString();
    staffData.Timestamp = new Date().toISOString();
    staffData.College = "Bon Secours College for Women";
    
    // Check if staff already exists (same name and academic year)
    const existingIndex = allStaffData.findIndex(item => 
      item.StaffName === staffData.StaffName && 
      item.AcademicYear === staffData.AcademicYear
    );
    
    if (existingIndex >= 0) {
      // Update existing record
      allStaffData[existingIndex] = staffData;
      showMessage("Data updated successfully!", 'success');
    } else {
      // Add new record
      allStaffData.push(staffData);
      showMessage("Data saved successfully! Total records: " + allStaffData.length, 'success');
    }
    
    // Save to localStorage
    saveAllStaffData();
    return true;
  } catch(e) {
    console.error("Error saving data:", e);
    showMessage("Error saving data: " + e.message, 'error');
    return false;
  }
}

function deleteStaffRecord(index) {
  if (!confirm("Delete this staff record?")) return;
  
  allStaffData.splice(index, 1);
  saveAllStaffData();
  showMessage("Record deleted.", 'warning');
  viewAllStaffData();
}

function clearAllData() {
  if (!confirm("Clear ALL staff data? This cannot be undone!")) return;
  
  if (isLocalStorageAvailable()) {
    localStorage.removeItem('staffAppraisalData');
    allStaffData = [];
    showMessage("All data cleared.", 'warning');
    if (isAdminMode) viewAllStaffData();
  }
}

function backupData() {
  const dataStr = JSON.stringify(allStaffData, null, 2);
  const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
  const exportFileDefaultName = `BonSecours_Staff_Appraisal_Backup_${new Date().toISOString().slice(0,10)}.json`;
  
  const linkElement = document.createElement('a');
  linkElement.setAttribute('href', dataUri);
  linkElement.setAttribute('download', exportFileDefaultName);
  linkElement.click();
  
  showMessage("Backup downloaded as JSON file.", 'success');
}

function restoreData() {
  const input = document.createElement('input');
  input.type = 'file';
  input.accept = '.json';
  
  input.onchange = function(event) {
    const file = event.target.files[0];
    const reader = new FileReader();
    
    reader.onload = function(e) {
      try {
        const restoredData = JSON.parse(e.target.result);
        if (Array.isArray(restoredData)) {
          allStaffData = restoredData;
          saveAllStaffData();
          showMessage("Data restored successfully! Records: " + allStaffData.length, 'success');
          if (isAdminMode) viewAllStaffData();
        } else {
          showMessage("Invalid backup file format.", 'error');
        }
      } catch(err) {
        showMessage("Error parsing backup file: " + err.message, 'error');
      }
    };
    
    reader.readAsText(file);
  };
  
  input.click();
}

// ==================== MODE MANAGEMENT ====================
function switchToAdminMode() {
  document.getElementById('appraisalForm').style.display = 'none';
  document.getElementById('loginForm').style.display = 'block';
  document.getElementById('adminPassword').value = '';
  document.getElementById('adminPassword').focus();
}

function switchToStaffMode() {
  isAdminMode = false;
  document.getElementById('loginForm').style.display = 'none';
  document.getElementById('appraisalForm').style.display = 'block';
  document.getElementById('staffActions').classList.remove('hidden');
  document.getElementById('adminActions').classList.add('hidden');
  document.getElementById('adminPanel').classList.add('hidden');
  document.getElementById('switchModeBtn').style.display = 'block';
  showMessage("Switched to Staff Mode", 'info');
}

function loginAsAdmin() {
  const password = document.getElementById('adminPassword').value;
  if (password === ADMIN_PASSWORD) {
    isAdminMode = true;
    document.getElementById('loginForm').style.display = 'none';
    document.getElementById('appraisalForm').style.display = 'block';
    document.getElementById('staffActions').classList.add('hidden');
    document.getElementById('adminActions').classList.remove('hidden');
    document.getElementById('adminPanel').classList.remove('hidden');
    document.getElementById('switchModeBtn').style.display = 'none';
    
    // Load and display all data
    loadAllStaffData();
    viewAllStaffData();
    showMessage("Admin login successful! Total records: " + allStaffData.length, 'success');
  } else {
    showMessage("Incorrect password! Try: admin123", 'error');
  }
}

// ==================== ADMIN FUNCTIONS ====================
function viewAllStaffData() {
  allStaffData = loadAllStaffData();
  const display = document.getElementById('adminDataDisplay');
  
  if (allStaffData.length === 0) {
    display.innerHTML = '<p style="padding:20px; text-align:center; color:#666;">No staff data found. Switch to Staff Mode to add data.</p>';
    return;
  }
  
  // Calculate statistics
  const totalScores = allStaffData.map(staff => staff.TotalScore || 0);
  const avgScore = totalScores.length > 0 ? 
    Math.round((totalScores.reduce((a, b) => a + b, 0) / totalScores.length) * 10) / 10 : 0;
  
  let html = `
    <div style="background:linear-gradient(135deg, #0b486b 0%, #1c6ea4 100%); color:white; padding:12px; border-radius:5px; margin-bottom:15px;">
      <strong>Bon Secours College Statistics:</strong> 
      Total Records: <strong>${allStaffData.length}</strong> | 
      Average Score: <strong>${avgScore}/200</strong> |
      Highest: <strong>${Math.max(...totalScores)}</strong> | 
      Lowest: <strong>${Math.min(...totalScores)}</strong>
    </div>
  `;
  
  html += '<div class="data-table"><table>';
  html += '<thead><tr>';
  html += '<th>No.</th>';
  html += '<th>Staff Name</th>';
  html += '<th>Department</th>';
  html += '<th>Designation</th>';
  html += '<th>Academic Year</th>';
  html += '<th>Total Score</th>';
  html += '<th>Performance</th>';
  html += '<th>Reviewer Remarks</th>';
  html += '<th>HOD Remarks</th>';
  html += '<th>Principal Remarks</th>';
  html += '<th>Date Saved</th>';
  html += '<th>Actions</th>';
  html += '</tr></thead><tbody>';
  
  allStaffData.forEach((staff, index) => {
    const score = staff.TotalScore || 0;
    const rowClass = score >= 150 ? 'highlight' : '';
    const reviewerRemarks = staff.reviewer_remarks ? staff.reviewer_remarks.substring(0, 30) + (staff.reviewer_remarks.length > 30 ? '...' : '') : '-';
    const hodRemarks = staff.hod_remarks ? staff.hod_remarks.substring(0, 30) + (staff.hod_remarks.length > 30 ? '...' : '') : '-';
    const principalRemarks = staff.principal_remarks ? staff.principal_remarks.substring(0, 30) + (staff.principal_remarks.length > 30 ? '...' : '') : '-';
    
    html += `<tr class="${rowClass}">`;
    html += `<td>${index + 1}</td>`;
    html += `<td><strong>${staff.StaffName || 'N/A'}</strong></td>`;
    html += `<td>${staff.Department || 'N/A'}</td>`;
    html += `<td>${staff.Designation || 'N/A'}</td>`;
    html += `<td>${staff.AcademicYear || 'N/A'}</td>`;
    html += `<td class="score"><strong>${score}</strong></td>`;
    html += `<td>${getPerformanceLevel(score)}</td>`;
    html += `<td title="${staff.reviewer_remarks || ''}">${reviewerRemarks}</td>`;
    html += `<td title="${staff.hod_remarks || ''}">${hodRemarks}</td>`;
    html += `<td title="${staff.principal_remarks || ''}">${principalRemarks}</td>`;
    html += `<td>${staff.SaveDate || 'N/A'}</td>`;
    html += `<td>
      <button onclick="viewStaffDetails(${index})" style="padding:4px 8px; font-size:12px; margin-right:5px;">👁️ View</button>
      <button onclick="deleteStaffRecord(${index})" class="danger" style="padding:4px 8px; font-size:12px;">🗑️ Delete</button>
    </td>`;
    html += '</tr>';
  });
  
  html += '</tbody></table></div>';
  display.innerHTML = html;
}

function viewStaffDetails(index) {
  const staff = allStaffData[index];
  const preview = document.getElementById('preview');
  preview.style.display = 'block';
  
  let html = `<h3>📋 Staff Details: ${staff.StaffName}</h3>`;
  html += `<p><strong>College:</strong> Bon Secours College for Women</p>`;
  html += `<p><strong>Department:</strong> ${staff.Department} | <strong>Designation:</strong> ${staff.Designation} | <strong>Year:</strong> ${staff.AcademicYear}</p>`;
  html += `<p><strong>Total Score:</strong> <span class="score">${staff.TotalScore}/200</span> | <strong>Performance:</strong> ${getPerformanceLevel(staff.TotalScore)}</p>`;
  html += `<p><strong>Saved on:</strong> ${staff.SaveDate}</p>`;
  
  if (staff.Breakdown) {
    html += '<h4>📊 Score Breakdown:</h4>';
    html += '<table><tr><th>Section</th><th>Score</th><th>Max Score</th><th>Remarks</th></tr>';
    
    for (const [key, value] of Object.entries(staff.Breakdown)) {
      const name = SECTION_NAMES[key] || key;
      const maxScore = name.includes('(Max:') ? name.match(/\(Max: (.*?)\)/)?.[1] || '' : '';
      const remarks = getSectionRemarks(key, value);
      html += `<tr><td>${name.split(' (')[0]}</td><td class="score">${value}</td><td>${maxScore}</td><td>${remarks}</td></tr>`;
    }
    
    html += `<tr style="background:#f0f0f0; font-weight:bold;">
      <td>TOTAL</td>
      <td>${staff.TotalScore}</td>
      <td>200</td>
      <td>${getPerformanceLevel(staff.TotalScore)}</td>
    </tr>`;
    html += '</table>';
  }
  
  // Display remarks if available
  if (staff.reviewer_remarks || staff.hod_remarks || staff.principal_remarks || staff.recommendations) {
    html += '<h4>📝 Remarks & Recommendations:</h4>';
    if (staff.reviewer_remarks) html += `<p><strong>Reviewer Remarks:</strong> ${staff.reviewer_remarks}</p>`;
    if (staff.hod_remarks) html += `<p><strong>HOD Remarks:</strong> ${staff.hod_remarks}</p>`;
    if (staff.principal_remarks) html += `<p><strong>Principal Remarks:</strong> ${staff.principal_remarks}</p>`;
    if (staff.recommendations) html += `<p><strong>Recommendations:</strong> ${staff.recommendations}</p>`;
  }
  
  if (staff.strengths || staff.weaknesses) {
    html += '<h4>📝 Self Assessment:</h4>';
    if (staff.strengths) html += `<p><strong>Strengths:</strong> ${staff.strengths}</p>`;
    if (staff.weaknesses) html += `<p><strong>Areas for Improvement:</strong> ${staff.weaknesses}</p>`;
  }
  
  html += `<div style="margin-top:20px;">
    <button onclick="exportStaffExcel(${index})" class="admin" style="margin-right:10px;">📥 Export This Record</button>
    <button onclick="loadStaffIntoForm(${index})" class="secondary">📝 Load into Form</button>
  </div>`;
  
  preview.innerHTML = html;
}

function getSectionRemarks(key, value) {
  const remarks = {
    section1: value >= 10 ? 'Excellent attendance' : value >= 5 ? 'Good attendance' : 'Needs improvement',
    section2: value >= 15 ? 'Excellent professional growth' : value >= 10 ? 'Good development' : 'Needs more activities',
    section8: value >= 15 ? 'Outstanding teaching performance' : value >= 10 ? 'Good teaching' : 'Average teaching',
    section17: value >= 4 ? 'Excellent results' : value >= 3 ? 'Good results' : 'Needs improvement',
    section18: value >= 4 ? 'Excellent attendance maintenance' : value >= 3 ? 'Good attendance' : 'Needs improvement',
    section23_24: value >= 10 ? 'Active researcher' : value >= 5 ? 'Moderate research' : 'Limited research',
    section25_27: value >= 10 ? 'Strong leadership' : value >= 5 ? 'Good involvement' : 'Limited involvement'
  };
  
  return remarks[key] || '–';
}

function exportStaffExcel(index) {
  const staff = allStaffData[index];
  
  const exportData = [{
    'College': 'Bon Secours College for Women',
    'Staff Name': staff.StaffName || '',
    'Department': staff.Department || '',
    'Designation': staff.Designation || '',
    'Academic Year': staff.AcademicYear || '',
    'Email ID': staff.email || '',
    'Employee ID': staff.emp_id || '',
    'Total Score': staff.TotalScore || 0,
    'Performance Level': getPerformanceLevel(staff.TotalScore),
    'Overall Remarks': getPerformanceRemarks(staff.TotalScore),
    'Save Date': staff.SaveDate || '',
    'Strengths': staff.strengths || '',
    'Areas for Improvement': staff.weaknesses || '',
    'Additional Achievements': staff.achievements || '',
    'Future Goals': staff.future_goals || '',
    'Reviewer Remarks': staff.reviewer_remarks || '',
    'HOD Remarks': staff.hod_remarks || '',
    'Principal Remarks': staff.principal_remarks || '',
    'Overall Recommendations': staff.recommendations || ''
  }];
  
  // Add breakdown scores with proper section names
  if (staff.Breakdown) {
    for (const [key, value] of Object.entries(staff.Breakdown)) {
      const sectionName = SECTION_NAMES[key] || key;
      exportData[0][sectionName] = value;
      exportData[0][sectionName + ' Remarks'] = getSectionRemarks(key, value);
    }
  }
  
  try {
    const ws = XLSX.utils.json_to_sheet(exportData);
    const wb = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(wb, ws, 'Staff Appraisal');
    
    // Auto-adjust column widths
    const wscols = Object.keys(exportData[0]).map(() => ({wch: 20}));
    ws['!cols'] = wscols;
    
    const filename = `BonSecours_Staff_${staff.StaffName.replace(/\s+/g, '_')}_${staff.AcademicYear}.xlsx`;
    XLSX.writeFile(wb, filename);
    showMessage("Excel file exported for " + staff.StaffName, 'success');
  } catch(e) {
    showMessage("Error exporting Excel: " + e.message, 'error');
  }
}

function exportAllStaffExcel() {
  if (allStaffData.length === 0) {
    showMessage("No data to export.", 'warning');
    return;
  }
  
  const exportData = allStaffData.map(staff => {
    const row = {
      'College': 'Bon Secours College for Women',
      'Staff Name': staff.StaffName || '',
      'Department': staff.Department || '',
      'Designation': staff.Designation || '',
      'Academic Year': staff.AcademicYear || '',
      'Email ID': staff.email || '',
      'Employee ID': staff.emp_id || '',
      'Total Score': staff.TotalScore || 0,
      'Performance Level': getPerformanceLevel(staff.TotalScore),
      'Overall Remarks': getPerformanceRemarks(staff.TotalScore),
      'Save Date': staff.SaveDate || '',
      'Strengths': staff.strengths || '',
      'Areas for Improvement': staff.weaknesses || '',
      'Reviewer Remarks': staff.reviewer_remarks || '',
      'HOD Remarks': staff.hod_remarks || '',
      'Principal Remarks': staff.principal_remarks || ''
    };
    
    // Add breakdown scores if available with proper names
    if (staff.Breakdown) {
      for (const [key, value] of Object.entries(staff.Breakdown)) {
        const sectionName = SECTION_NAMES[key] || key;
        row[sectionName] = value;
      }
    }
    
    return row;
  });
  
  try {
    const ws = XLSX.utils.json_to_sheet(exportData);
    const wb = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(wb, ws, 'All Staff Data');
    
    // Auto-adjust column widths
    const maxColumns = Math.max(...exportData.map(row => Object.keys(row).length));
    const wscols = new Array(maxColumns).fill({wch: 20});
    ws['!cols'] = wscols;
    
    const filename = `BonSecours_All_Staff_Appraisal_${new Date().toISOString().slice(0,10)}.xlsx`;
    XLSX.writeFile(wb, filename);
    showMessage("All staff data exported to Excel!", 'success');
  } catch(e) {
    showMessage("Error exporting Excel: " + e.message, 'error');
  }
}

function searchStaffData() {
  const searchTerm = document.getElementById('searchInput').value.toLowerCase();
  allStaffData = loadAllStaffData();
  
  if (!searchTerm) {
    viewAllStaffData();
    return;
  }
  
  const filteredData = allStaffData.filter(staff => 
    (staff.StaffName && staff.StaffName.toLowerCase().includes(searchTerm)) ||
    (staff.Department && staff.Department.toLowerCase().includes(searchTerm)) ||
    (staff.Designation && staff.Designation.toLowerCase().includes(searchTerm)) ||
    (staff.AcademicYear && staff.AcademicYear.toLowerCase().includes(searchTerm))
  );
  
  const display = document.getElementById('adminDataDisplay');
  
  if (filteredData.length === 0) {
    display.innerHTML = `<p style="padding:20px; text-align:center; color:#666;">No results found for "${searchTerm}"</p>`;
    return;
  }
  
  let html = `<p style="color:#666;">🔍 Search results for "${searchTerm}": ${filteredData.length} records found</p>`;
  html += '<div class="data-table"><table>';
  html += '<thead><tr><th>No.</th><th>Staff Name</th><th>Department</th><th>Designation</th><th>Academic Year</th><th>Total Score</th><th>Performance</th><th>Reviewer Remarks</th><th>Date Saved</th><th>Actions</th></tr></thead><tbody>';
  
  filteredData.forEach((staff, index) => {
    const reviewerRemarks = staff.reviewer_remarks ? staff.reviewer_remarks.substring(0, 30) + (staff.reviewer_remarks.length > 30 ? '...' : '') : '-';
    
    html += `<tr>`;
    html += `<td>${index + 1}</td>`;
    html += `<td><strong>${staff.StaffName || 'N/A'}</strong></td>`;
    html += `<td>${staff.Department || 'N/A'}</td>`;
    html += `<td>${staff.Designation || 'N/A'}</td>`;
    html += `<td>${staff.AcademicYear || 'N/A'}</td>`;
    html += `<td class="score"><strong>${staff.TotalScore || 0}</strong></td>`;
    html += `<td>${getPerformanceLevel(staff.TotalScore)}</td>`;
    html += `<td title="${staff.reviewer_remarks || ''}">${reviewerRemarks}</td>`;
    html += `<td>${staff.SaveDate || 'N/A'}</td>`;
    html += `<td>
      <button onclick="viewStaffDetails(${allStaffData.indexOf(staff)})" style="padding:4px 8px; font-size:12px;">👁️ View</button>
    </td>`;
    html += '</tr>';
  });
  
  html += '</tbody></table></div>';
  display.innerHTML = html;
}

function loadStaffIntoForm(index) {
  const staff = allStaffData[index];
  
  // Set personal info
  document.getElementById('staff_name').value = staff.StaffName || '';
  document.getElementById('dept').value = staff.Department || '';
  document.getElementById('designation').value = staff.Designation || '';
  document.getElementById('acyear').value = staff.AcademicYear || '';
  document.getElementById('email').value = staff.email || '';
  document.getElementById('emp_id').value = staff.emp_id || '';
  
  // Set text areas
  document.getElementById('strengths').value = staff.strengths || '';
  document.getElementById('weaknesses').value = staff.weaknesses || '';
  document.getElementById('achievements').value = staff.achievements || '';
  document.getElementById('future_goals').value = staff.future_goals || '';
  
  // Set remarks
  document.getElementById('reviewer_remarks').value = staff.reviewer_remarks || '';
  document.getElementById('hod_remarks').value = staff.hod_remarks || '';
  document.getElementById('principal_remarks').value = staff.principal_remarks || '';
  document.getElementById('recommendations').value = staff.recommendations || '';
  
  // Show preview with existing data
  const preview = document.getElementById('preview');
  preview.style.display = 'block';
  preview.innerHTML = `<h3>📝 Data Loaded: ${staff.StaffName}</h3>
    <p>Staff data loaded into form. You can now edit and save changes.</p>
    <p><strong>College:</strong> Bon Secours College for Women</p>
    <p><strong>Current Score:</strong> <span class="score">${staff.TotalScore || 0}/200</span></p>
    <p><strong>Performance:</strong> ${getPerformanceLevel(staff.TotalScore || 0)}</p>`;
  
  showMessage("Staff data loaded into form. Edit and save if needed.", 'info');
  switchToStaffMode();
}

function viewMyData() {
  const staffName = document.getElementById('staff_name').value;
  const acYear = document.getElementById('acyear').value;
  
  if (!staffName) {
    showMessage("Please enter your name first.", 'warning');
    return;
  }
  
  allStaffData = loadAllStaffData();
  const myData = allStaffData.filter(staff => 
    staff.StaffName.toLowerCase() === staffName.toLowerCase() && 
    (!acYear || staff.AcademicYear === acYear)
  );
  
  const preview = document.getElementById('preview');
  preview.style.display = 'block';
  
  if (myData.length === 0) {
    preview.innerHTML = `<h3>📋 My Saved Data</h3>
      <p>No saved data found for "${staffName}"${acYear ? ' in ' + acYear : ''}.</p>
      <p><strong>College:</strong> Bon Secours College for Women</p>
      <p>Fill the form and click "Save Data" to store your appraisal.</p>`;
    return;
  }
  
  let html = `<h3>📋 My Saved Data (${myData.length} records)</h3>
    <p><strong>College:</strong> Bon Secours College for Women</p>`;
  
  myData.forEach((data, index) => {
    html += `<div style="background:#f8f9fa; padding:15px; margin:10px 0; border-radius:5px; border-left:4px solid #0077cc;">
      <h4>📄 Record ${index + 1}: ${data.AcademicYear}</h4>
      <p><strong>Department:</strong> ${data.Department} | <strong>Designation:</strong> ${data.Designation}</p>
      <p><strong>Total Score:</strong> <span class="score">${data.TotalScore || 0}/200</span></p>
      <p><strong>Performance:</strong> ${getPerformanceLevel(data.TotalScore || 0)}</p>`;
    
    if (data.reviewer_remarks || data.hod_remarks || data.principal_remarks) {
      html += `<p><strong>Remarks:</strong> `;
      if (data.reviewer_remarks) html += `Reviewer: ${data.reviewer_remarks.substring(0, 50)}${data.reviewer_remarks.length > 50 ? '...' : ''} `;
      if (data.hod_remarks) html += `HOD: ${data.hod_remarks.substring(0, 50)}${data.hod_remarks.length > 50 ? '...' : ''} `;
      html += `</p>`;
    }
    
    html += `<p><strong>Saved on:</strong> ${data.SaveDate}</p>
      <div style="margin-top:10px;">
        <button onclick="loadStaffIntoForm(${allStaffData.indexOf(data)})" style="margin-right:10px;">📝 Load This</button>
        <button onclick="deleteStaffRecord(${allStaffData.indexOf(data)})" class="danger">🗑️ Delete</button>
      </div>
    </div>`;
  });
  
  preview.innerHTML = html;
}

// ==================== SCORING FUNCTIONS ====================
function calculateScores() {
  // Collect all form data
  const formData = {
    // Personal info
    StaffName: document.getElementById('staff_name').value.trim(),
    Department: document.getElementById('dept').value.trim(),
    Designation: document.getElementById('designation').value.trim(),
    AcademicYear: document.getElementById('acyear').value.trim(),
    email: document.getElementById('email').value.trim(),
    emp_id: document.getElementById('emp_id').value.trim(),
    
    // Section 1
    cl_days: parseInt(document.getElementById('cl_days').value) || 0,
    lop_days: parseInt(document.getElementById('lop_days').value) || 0,
    perm_count: parseInt(document.getElementById('perm_count').value) || 0,
    onduty_days: parseInt(document.getElementById('onduty_days').value) || 0,
    onduty_proof: hasFiles('onduty_proof'),
    
    // Section 2
    qual_upg: parseInt(document.getElementById('qual_upg').value) || 0,
    qual_proof: hasFiles('qual_proof'),
    fdp_days: parseInt(document.getElementById('fdp_days').value) || 0,
    fdp_proof: hasFiles('fdp_proof'),
    seminar_att: parseInt(document.getElementById('seminar_att').value) || 0,
    seminar_proof: hasFiles('seminar_proof'),
    seminar_org: parseInt(document.getElementById('seminar_org').value) || 0,
    seminar_org_proof: hasFiles('seminar_org_proof'),
    
    // Section 3
    online_courses: parseInt(document.getElementById('online_courses').value) || 0,
    online_proof: hasFiles('online_proof'),
    econtent_count: parseInt(document.getElementById('econtent_count').value) || 0,
    
    // Section 4
    awards_count: parseInt(document.getElementById('awards_count').value) || 0,
    awards_proof: hasFiles('awards_proof'),
    
    // Section 5
    memberships: parseInt(document.getElementById('memberships').value) || 0,
    memberships_proof: hasFiles('memberships_proof'),
    
    // Section 6
    admin_action: parseInt(document.getElementById('admin_action').value) || 0,
    
    // Section 7
    curriculum_count: parseInt(document.getElementById('curriculum_count').value) || 0,
    curriculum_proof: hasFiles('curriculum_proof'),
    
    // Section 8
    workload: parseInt(document.getElementById('workload').value) || 0,
    courses_taught: parseInt(document.getElementById('courses_taught').value) || 0,
    remedial: parseInt(document.getElementById('remedial').value) || 0,
    examduties: parseInt(document.getElementById('examduties').value) || 0,
    coursefile_sub: parseInt(document.getElementById('coursefile_sub').value) || 0,
    coursefile_proof: hasFiles('coursefile_proof'),
    
    // Section 9
    value_courses: parseInt(document.getElementById('value_courses').value) || 0,
    value_proof: hasFiles('value_proof'),
    
    // Section 10
    co_curricular: parseInt(document.getElementById('co_curricular').value) || 0,
    co_curricular_proof: hasFiles('co_curricular_proof'),
    
    // Section 11
    extra_activities: parseInt(document.getElementById('extra_activities').value) || 0,
    extra_proof: hasFiles('extra_proof'),
    
    // Section 12
    social_prog: parseInt(document.getElementById('social_prog').value) || 0,
    social_proof: hasFiles('social_proof'),
    
    // Section 13
    projects_guided: parseInt(document.getElementById('projects_guided').value) || 0,
    projects_proof: hasFiles('projects_proof'),
    
    // Section 14
    internships: parseInt(document.getElementById('internships').value) || 0,
    internships_proof: hasFiles('internships_proof'),
    
    // Section 15
    mentees: parseInt(document.getElementById('mentees').value) || 0,
    mentees_proof: hasFiles('mentees_proof'),
    
    // Section 16
    incharge: parseInt(document.getElementById('incharge').value) || 0,
    
    // Section 17
    pass_percent: parseInt(document.getElementById('pass_percent').value) || 0,
    pass_proof: hasFiles('pass_proof'),
    
    // Section 18
    stud_att_percent: parseInt(document.getElementById('stud_att_percent').value) || 0,
    stud_att_proof: hasFiles('stud_att_proof'),
    
    // Section 19
    exam_att_percent: parseInt(document.getElementById('exam_att_percent').value) || 0,
    exam_att_proof: hasFiles('exam_att_proof'),
    
    // Section 20
    parent_meet: parseInt(document.getElementById('parent_meet').value) || 0,
    parent_proof: hasFiles('parent_proof'),
    
    // Section 21
    slow_learners: parseInt(document.getElementById('slow_learners').value) || 0,
    slow_proof: hasFiles('slow_proof'),
    
    // Section 22
    adv_learners: parseInt(document.getElementById('adv_learners').value) || 0,
    adv_proof: hasFiles('adv_proof'),
    
    // Section 23-24
    research_papers: parseInt(document.getElementById('research_papers').value) || 0,
    research_projects: parseInt(document.getElementById('research_projects').value) || 0,
    research_proof: hasFiles('research_proof'),
    
    // Section 25-27
    leadership_roles: parseInt(document.getElementById('leadership_roles').value) || 0,
    files_maint: parseInt(document.getElementById('files_maint').value) || 0,
    leadership_proof: hasFiles('leadership_proof'),
    
    // Text fields
    strengths: document.getElementById('strengths').value,
    weaknesses: document.getElementById('weaknesses').value,
    achievements: document.getElementById('achievements').value,
    future_goals: document.getElementById('future_goals').value,
    
    // Remarks fields
    reviewer_remarks: document.getElementById('reviewer_remarks').value,
    hod_remarks: document.getElementById('hod_remarks').value,
    principal_remarks: document.getElementById('principal_remarks').value,
    recommendations: document.getElementById('recommendations').value
  };
  
  // Calculate scores
  const scores = {};
  let totalScore = 0;
  
  // Section 1: Leaves/On Duty (Max: ±12)
  let section1 = 10; // Base
  if (formData.cl_days > 12) section1 -= (formData.cl_days - 12);
  section1 -= formData.lop_days;
  if (formData.perm_count > 4) section1 -= Math.floor(formData.perm_count / 4);
  if (formData.onduty_days > 0 && formData.onduty_proof) {
    section1 += Math.min(formData.onduty_days, 5);
  }
  scores.section1 = Math.max(-10, Math.min(12, Math.round(section1 * 10) / 10));
  totalScore += scores.section1;
  
  // Section 2: Professional Development (Max: 20)
  let section2 = 0;
  if (formData.qual_upg > 0 && formData.qual_proof) section2 += formData.qual_upg;
  if (formData.fdp_proof) section2 += Math.min(formData.fdp_days, 5);
  if (formData.seminar_proof) section2 += Math.min(formData.seminar_att * 2.5, 5);
  if (formData.seminar_org_proof) section2 += Math.min(formData.seminar_org * 5, 5);
  scores.section2 = Math.min(20, Math.round(section2 * 10) / 10);
  totalScore += scores.section2;
  
  // Section 3: Online Courses (Max: 10)
  let section3 = 0;
  if (formData.online_proof) section3 += Math.min(formData.online_courses * 5, 5);
  section3 += Math.min(formData.econtent_count * 5, 5);
  scores.section3 = Math.min(10, Math.round(section3 * 10) / 10);
  totalScore += scores.section3;
  
  // Section 4: Awards (Max: 5)
  scores.section4 = formData.awards_proof ? Math.min(formData.awards_count * 5, 5) : 0;
  totalScore += scores.section4;
  
  // Section 5: Memberships (Max: 5)
  scores.section5 = formData.memberships_proof ? Math.min(formData.memberships * 5, 5) : 0;
  totalScore += scores.section5;
  
  // Section 6: Admin Actions (Max: -5)
  scores.section6 = formData.admin_action;
  totalScore += scores.section6;
  
  // Section 7: Curriculum (Max: 5)
  scores.section7 = formData.curriculum_proof ? Math.min(formData.curriculum_count * 5, 5) : 0;
  totalScore += scores.section7;
  
  // Section 8: Teaching (Max: 20)
  let section8 = 0;
  section8 += Math.min(formData.workload >= 15 ? 5 : formData.workload / 3, 5);
  section8 += Math.min(formData.courses_taught >= 3 ? 3 : formData.courses_taught, 3);
  section8 += Math.min(formData.remedial >= 10 ? 3 : formData.remedial / 3.33, 3);
  section8 += Math.min(formData.examduties >= 5 ? 3 : formData.examduties / 1.67, 3);
  if (formData.coursefile_sub > 0 && formData.coursefile_proof) section8 += 5;
  scores.section8 = Math.min(20, Math.round(section8 * 10) / 10);
  totalScore += scores.section8;
  
  // Section 9: Value Added (Max: 5)
  scores.section9 = formData.value_proof ? Math.min(formData.value_courses * 5, 5) : 0;
  totalScore += scores.section9;
  
  // Section 10: Co-curricular (Max: 5)
  scores.section10 = formData.co_curricular_proof ? Math.min(formData.co_curricular * 5, 5) : 0;
  totalScore += scores.section10;
  
  // Section 11: Extra-curricular (Max: 5)
  scores.section11 = formData.extra_proof ? Math.min(formData.extra_activities * 5, 5) : 0;
  totalScore += scores.section11;
  
  // Section 12: Social (Max: 5)
  scores.section12 = formData.social_proof ? Math.min(formData.social_prog * 5, 5) : 0;
  totalScore += scores.section12;
  
  // Section 13: Projects (Max: 5)
  scores.section13 = formData.projects_proof ? Math.min(formData.projects_guided * 5, 5) : 0;
  totalScore += scores.section13;
  
  // Section 14: Internships (Max: 5)
  scores.section14 = formData.internships_proof ? Math.min(formData.internships * 5, 5) : 0;
  totalScore += scores.section14;
  
  // Section 15: Mentorship (Max: 5)
  scores.section15 = (formData.mentees_proof && formData.mentees > 0) ? 5 : 0;
  totalScore += scores.section15;
  
  // Section 16: Class In-charge (Max: 5)
  scores.section16 = formData.incharge;
  totalScore += scores.section16;
  
  // Section 17: Results (Max: 5)
  if (formData.pass_proof) {
    if (formData.pass_percent >= 90) scores.section17 = 5;
    else if (formData.pass_percent >= 80) scores.section17 = 4;
    else if (formData.pass_percent >= 70) scores.section17 = 3;
    else if (formData.pass_percent >= 60) scores.section17 = 2;
    else scores.section17 = 1;
  } else {
    scores.section17 = 0;
  }
  totalScore += scores.section17;
  
  // Section 18: Attendance (Max: 5)
  if (formData.stud_att_proof) {
    if (formData.stud_att_percent >= 90) scores.section18 = 5;
    else if (formData.stud_att_percent >= 80) scores.section18 = 4;
    else if (formData.stud_att_percent >= 70) scores.section18 = 3;
    else if (formData.stud_att_percent >= 60) scores.section18 = 2;
    else scores.section18 = 1;
  } else {
    scores.section18 = 0;
  }
  totalScore += scores.section18;
  
  // Section 19: Exam Attendance (Max: 5)
  if (formData.exam_att_proof) {
    if (formData.exam_att_percent >= 95) scores.section19 = 5;
    else if (formData.exam_att_percent >= 85) scores.section19 = 4;
    else if (formData.exam_att_percent >= 75) scores.section19 = 3;
    else if (formData.exam_att_percent >= 60) scores.section19 = 2;
    else scores.section19 = 1;
  } else {
    scores.section19 = 0;
  }
  totalScore += scores.section19;
  
  // Section 20: Parent Meetings (Max: 5)
  scores.section20 = (formData.parent_proof && formData.parent_meet > 0) ? 5 : 0;
  totalScore += scores.section20;
  
  // Section 21: Slow Learners (Max: 5)
  scores.section21 = (formData.slow_proof && formData.slow_learners > 0) ? 5 : 0;
  totalScore += scores.section21;
  
  // Section 22: Advanced Learners (Max: 5)
  scores.section22 = (formData.adv_proof && formData.adv_learners > 0) ? 5 : 0;
  totalScore += scores.section22;
  
  // Section 23-24: Research (Max: 15)
  let section23_24 = 0;
  if (formData.research_proof) {
    section23_24 += Math.min(formData.research_papers * 2, 8);
    section23_24 += Math.min(formData.research_projects * 3.5, 7);
  }
  scores.section23_24 = Math.min(15, Math.round(section23_24 * 10) / 10);
  totalScore += scores.section23_24;
  
  // Section 25-27: Leadership (Max: 15)
  let section25_27 = 0;
  if (formData.leadership_proof) {
    section25_27 += Math.min(formData.leadership_roles * 2.33, 7);
  }
  section25_27 += formData.files_maint;
  section25_27 += Math.min(formData.leadership_roles * 1.5, 3);
  scores.section25_27 = Math.min(15, Math.round(section25_27 * 10) / 10);
  totalScore += scores.section25_27;
  
  // Final total
  totalScore = Math.max(0, Math.min(200, Math.round(totalScore * 10) / 10));
  
  // Create complete staff record
  const staffRecord = {
    ...formData,
    TotalScore: totalScore,
    Breakdown: scores,
    strengths: formData.strengths,
    weaknesses: formData.weaknesses,
    achievements: formData.achievements,
    future_goals: formData.future_goals,
    reviewer_remarks: formData.reviewer_remarks,
    hod_remarks: formData.hod_remarks,
    principal_remarks: formData.principal_remarks,
    recommendations: formData.recommendations
  };
  
  return staffRecord;
}

function displayPreview(summary) {
  const preview = document.getElementById('preview');
  preview.style.display = 'block';
  
  let html = `<h3>📊 Score Breakdown - Total: ${summary.TotalScore}/200</h3>`;
  html += `<p><strong>College:</strong> Bon Secours College for Women</p>`;
  html += `<p><strong>Name:</strong> ${summary.StaffName} | <strong>Dept:</strong> ${summary.Department} | <strong>Year:</strong> ${summary.AcademicYear}</p>`;
  html += `<p><strong>Performance Level:</strong> ${getPerformanceLevel(summary.TotalScore)}</p>`;
  
  html += '<table style="font-size:13px;">';
  html += '<tr style="background:#f8f9fa;"><th>Section</th><th>Score</th><th>Max Score</th><th>Remarks</th></tr>';
  
  for (const [key, value] of Object.entries(summary.Breakdown || {})) {
    const name = SECTION_NAMES[key] || key;
    const maxScore = name.includes('(Max:') ? name.match(/\(Max: (.*?)\)/)?.[1] || '' : '';
    const remarks = getSectionRemarks(key, value);
    html += `<tr><td>${name.split(' (')[0]}</td><td class="score">${value}</td><td>${maxScore}</td><td>${remarks}</td></tr>`;
  }
  
  html += `<tr style="background:#f0f0f0; font-weight:bold;">
    <td>TOTAL</td>
    <td>${summary.TotalScore}</td>
    <td>200</td>
    <td>${getPerformanceRemarks(summary.TotalScore)}</td>
  </tr>`;
  html += '</table>';
  
  preview.innerHTML = html;
  
  // Update total display
  document.getElementById('totalDisplay').innerText = `Total: ${summary.TotalScore}/200`;
}

function getPerformanceRemarks(score) {
  if (score >= 180) return 'Outstanding performance - Eligible for promotion';
  if (score >= 160) return 'Excellent performance - Recommended for rewards';
  if (score >= 140) return 'Very good performance - Continue good work';
  if (score >= 120) return 'Good performance - Room for improvement';
  if (score >= 100) return 'Satisfactory performance - Needs training';
  if (score >= 80) return 'Needs improvement - Requires mentoring';
  return 'Below expectations - Action plan needed';
}

function getPerformanceLevel(score) {
  if (score >= 180) return 'Outstanding Performance';
  if (score >= 160) return 'Excellent Performance';
  if (score >= 140) return 'Very Good Performance';
  if (score >= 120) return 'Good Performance';
  if (score >= 100) return 'Satisfactory Performance';
  if (score >= 80) return 'Needs Improvement';
  return 'Below Expectations';
}

function downloadExcel(summary) {
  try {
    if (!summary.StaffName) {
      showMessage("Please enter staff name first.", 'warning');
      return;
    }
    
    // Prepare data for Excel
    const row = {
      'College': 'Bon Secours College for Women',
      'Staff Name': summary.StaffName,
      'Department': summary.Department,
      'Designation': summary.Designation,
      'Academic Year': summary.AcademicYear,
      'Email ID': summary.email,
      'Employee ID': summary.emp_id,
      'Total Score': summary.TotalScore,
      'Performance Level': getPerformanceLevel(summary.TotalScore),
      'Overall Remarks': getPerformanceRemarks(summary.TotalScore),
      'Save Date': new Date().toLocaleString(),
      'Strengths': summary.strengths || '',
      'Areas for Improvement': summary.weaknesses || '',
      'Additional Achievements': summary.achievements || '',
      'Future Goals': summary.future_goals || '',
      'Reviewer Remarks': summary.reviewer_remarks || '',
      'HOD Remarks': summary.hod_remarks || '',
      'Principal Remarks': summary.principal_remarks || '',
      'Overall Recommendations': summary.recommendations || ''
    };
    
    // Add breakdown scores with proper section names
    if (summary.Breakdown) {
      for (const [key, value] of Object.entries(summary.Breakdown)) {
        const sectionName = SECTION_NAMES[key] || key;
        row[sectionName] = value;
        row[sectionName + ' Remarks'] = getSectionRemarks(key, value);
      }
    }
    
    // Create worksheet and workbook
    const ws = XLSX.utils.json_to_sheet([row]);
    const wb = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(wb, ws, 'Staff Appraisal');
    
    // Auto-adjust column widths
    const wscols = Object.keys(row).map(() => ({wch: 20}));
    ws['!cols'] = wscols;
    
    const filename = `BonSecours_Appraisal_${summary.StaffName.replace(/\s+/g, '_')}_${summary.AcademicYear}_${new Date().toISOString().slice(0,10)}.xlsx`;
    XLSX.writeFile(wb, filename);
    
    showMessage("Excel file downloaded with remarks and section names!", 'success');
  } catch(e) {
    showMessage("Error downloading Excel: " + e.message, 'error');
  }
}

function clearForm() {
  if (!confirm("Clear all form data?")) return;
  
  // Get all input elements
  const inputs = document.querySelectorAll('input[type="text"], input[type="number"], textarea');
  inputs.forEach(input => {
    input.value = '';
  });
  
  // Clear select elements
  const selects = document.querySelectorAll('select');
  selects.forEach(select => {
    select.selectedIndex = 0;
  });
  
  // Clear file inputs
  const fileInputs = document.querySelectorAll('input[type="file"]');
  fileInputs.forEach(input => input.value = '');
  
  // Hide preview
  document.getElementById('preview').style.display = 'none';
  document.getElementById('totalDisplay').innerText = '';
  
  showMessage("Form cleared.", 'info');
}

// ==================== INITIALIZE APPLICATION ====================
document.addEventListener('DOMContentLoaded', function() {
  console.log("Bon Secours College Staff Appraisal System Initialized");
  
  // Load existing data
  loadAllStaffData();
  
  // Initialize buttons
  document.getElementById('previewBtn').addEventListener('click', function() {
    console.log("Preview button clicked");
    const summary = calculateScores();
    displayPreview(summary);
  });
  
  document.getElementById('calcBtn').addEventListener('click', function() {
    console.log("Calculate & Download button clicked");
    const summary = calculateScores();
    displayPreview(summary);
    downloadExcel(summary);
  });
  
  document.getElementById('saveToLocalBtn').addEventListener('click', function() {
    console.log("Save button clicked");
    const summary = calculateScores();
    if (saveStaffData(summary)) {
      displayPreview(summary);
    }
  });
  
  document.getElementById('viewMyDataBtn').addEventListener('click', function() {
    console.log("View My Data button clicked");
    viewMyData();
  });
  
  document.getElementById('clearFormBtn').addEventListener('click', clearForm);
  
  // Initialize in staff mode
  switchToStaffMode();
  
  console.log("Application ready. Total records loaded: " + allStaffData.length);
});
</script>
</body>
</html>
