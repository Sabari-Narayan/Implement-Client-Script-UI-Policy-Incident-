# 🛠️ Implement Client Script & UI Policy (Incident)

> **Naan Mudhalvan | ServiceNow University Micro Project**

A ServiceNow micro project demonstrating how **UI Policies** and **Client Scripts** enforce data integrity, automate field behavior, and validate user input on the **Incident** form — ensuring accurate triage, routing, and resolution.

---

## 📌 Project Details

| Field | Details |
|:---|:---|
| **Team ID** | `6ab636abdcdae33acb393f Fc1` |
| **Platform** | ServiceNow (Personal Developer Instance) |
| **College** | SACS MAVMM Engineering College |
| **Department** | B.E. Computer Science and Engineering |
| **Year / Semester** | 3rd Year / 5th Semester |
| **Academic Year** | 2026–2027 (Odd Semester) |

### 👥 Team Members

| Name | Role |
|:---|:---|
| **Sabari Narayanan S** | Team Leader |
| Buvanesh G | Member |
| Vikas Samuel S | Member |
| G Haris | Member |

---

## 🎯 Problem Statement

Incident records frequently contain **incomplete or incorrect data** because the standard form lacks client-side enforcement of business rules. Agents can submit high-impact incidents without assigning a technician or may set incorrect urgency values — leading to **SLA breaches**, inaccurate reporting, and delayed resolutions.

## 💡 Solution

Implement **2 UI Policies** and **3 Client Scripts** on the Incident form to:

- ✅ Dynamically make fields **mandatory** based on conditions
- ✅ **Auto-populate** field values when related fields change
- ✅ Control field **read-only** behavior
- ✅ **Prevent invalid submissions** at save time
- ✅ **Validate list view edits** in real-time

---

## ⚙️ Implementations

### UI Policies

| # | UI Policy | Condition | Action |
|---|:---|:---|:---|
| 1 | Make Assigned To Mandatory | Impact = `1 - High` | Assigned To → **Mandatory = true** |
| 2 | Make Urgency Read-Only | Impact = `1 - High` | Urgency → **Read Only = true**, Value = `1 - High` |

### Client Scripts

#### 1️⃣ onChange — Auto-Populate Urgency
```javascript
function onChange(control, oldValue, newValue, isLoading) {
    if (isLoading || newValue === '') return;
    if (newValue == '1') {
        g_form.setValue('urgency', '1');
        g_form.showFieldMsg('urgency', 'Urgency auto-set to High based on Impact', 'info');
    }
}
```

#### 2️⃣ onSubmit — Validate Before Save
```javascript
function onSubmit() {
    var impact = g_form.getValue('impact');
    var assignedTo = g_form.getValue('assigned_to');
    if (impact == '1' && assignedTo == '') {
        g_form.showFieldMsg('assigned_to',
            'Assigned To is required for High Impact incidents', 'error');
        return false;
    }
    return true;
}
```

#### 3️⃣ onCellEdit — List View Validation
```javascript
function onCellEdit(sysIDs, table, oldValues, newValue, callback) {
    var validValues = ['1', '2', '3'];
    if (table == 'incident' && !validValues.includes(newValue)) {
        callback(false, 'Invalid value. Please select a valid option.');
    } else {
        callback(true);
    }
}
```

---

## 🧰 Technology Stack

| Component | Technology |
|:---|:---|
| Platform | ServiceNow (PDI — Washington/Xanadu) |
| Scripting Language | JavaScript (Client-Side) |
| API | GlideForm (`g_form`), GlideUser (`g_user`) |
| UI Framework | ServiceNow UI16 / Form Designer |
| Database | ServiceNow CMDB (MariaDB backend) |
| Development Tools | ServiceNow Script Editor / Studio |
| Testing | Chrome DevTools, ServiceNow ATF |

---

## 📁 Repository Structure

```
📦 AI-ML-and-GEN-AI-Track-Project-Template-main
│
├── 📂 1. Brainstorming & Ideation
│   ├── Brainstorming & Idea Prioritization.pdf
│   ├── Define Problem Statements.pdf
│   └── Empathy Map.pdf
│
├── 📂 2. Requirement Analysis
│   ├── Customer Journey Map.pdf
│   ├── Data Flow Diagram.pdf
│   ├── Solution Requirements.pdf
│   └── Technology Stack.pdf
│
├── 📂 3. Project Design Phase
│   ├── Problem-Solution Fit.pdf
│   ├── Proposed Solution.pdf
│   └── Solution Architecture.pdf
│
├── 📂 4. Project Planning Phase
│   └── Project Planning.pdf
│
├── 📂 5. Project Development Phase
│   ├── Code-Layout, Readability and Reusability.pdf
│   ├── Coding & Solution.pdf
│   └── No. of Functional Features Included in the Solution.pdf
│
├── 📂 6. Project Testing
│   └── Performance Testing.pdf
│
├── 📂 7. Project Documentation
│   ├── Project Executable Files.pdf
│   └── Sample Project Documentation.pdf    ← Full Project Report
│
├── 📂 8. Project Demonstration
│   ├── Communication.pdf
│   ├── Demonstration of Proposed Features.pdf
│   ├── Project Demo Planning.pdf
│   ├── Scalability & Future Plan.pdf
│   └── Team Involvement in Demonstration.pdf
│
└── README.md
```

---

## 🧪 Testing Summary

| Test Case | Expected Result | Status |
|:---|:---|:---:|
| Set Impact = High → Assigned To becomes mandatory | ✅ Mandatory indicator appears | **Pass** |
| Set Impact = High → Urgency auto-sets to High & read-only | ✅ Auto-populated & locked | **Pass** |
| Submit without Assigned To (Impact = High) | ✅ Save blocked with error | **Pass** |
| Edit invalid value from list view | ✅ Edit rejected with message | **Pass** |

> **Result:** 4/4 test cases passed · 0% error rate · Avg response time: 0.8s

---

## 🔮 Future Scope

- 🔄 Extend to **Change, Problem, and Request** modules
- ⚙️ Add server-side **Business Rules** for dual-layer validation
- 🤖 Implement **Flow Designer** for automated routing & escalation
- 🔐 ACL-based **field security** for role-based enforcement
- 🌐 **Service Portal** widgets with custom client-side validation
- 📊 **Performance Analytics** dashboards for data quality metrics

---

## 📚 References

1. [ServiceNow Docs — UI Policies](https://docs.servicenow.com/bundle/washingtondc-platform-administration/page/administer/form-administration/concept/c_UIPolicies.html)
2. [ServiceNow Docs — Client Scripts](https://docs.servicenow.com/bundle/washingtondc-platform-administration/page/script/client-scripts/concept/c_ClientScripts.html)
3. ServiceNow Developer Training — Client-Side Scripting
4. ITIL Foundation — Incident Management Best Practices
5. Naan Mudhalvan — ServiceNow Learning Track

---

## 📜 License

This project is developed as part of the **Naan Mudhalvan Engineering Programme** for academic purposes.

---

<p align="center">
  <b>Made with ❤️ by Team 6ab636abdcdae33acb393f Fc1</b><br>
  SACS MAVMM Engineering College · B.E. CSE · 2026–2027
</p>
