# PeopleHome Partner Enterprise Portal

## Overview
Enterprise portal for managing Partner App operations, used by internal teams to monitor partners, track leads, and manage the partner ecosystem.

---

## User Roles & Access Matrix

### 1. Admin
- **Description**: Full system access, user management, configuration
- **Access**: All modules
- **Capabilities**:
  - View all partners across branches
  - Manage all leads
  - User management (add/edit/deactivate users)
  - Role assignment
  - System configuration
  - Reports & Analytics
  - Audit logs

### 2. Sales
- **Description**: Branch-level sales team members
- **Access**: Tagged partners and their leads only
- **Capabilities**:
  - View partners tagged to them
  - View leads from their partners
  - Update lead status (New → In Progress → Submitted → Approved/Rejected)
  - Add comments on leads
  - View partner performance metrics
  - Cannot modify partner details

### 3. RCU (Risk Containment Unit)
- **Description**: Risk and verification team
- **Access**: All partners for verification
- **Capabilities**:
  - Verify partner documents
  - Update partner verification status
  - Flag suspicious partners
  - View partner history
  - Document verification checklist
  - Cannot modify lead status

---

## Portal Screens

### 1. Login Screen
- Email/Username field
- Password field
- Role displayed post-login based on user credentials
- "Forgot Password" link
- Session management

### 2. Dashboard
**Admin View**:
- Total Partners (Active, Pending, Rejected)
- Total Leads (by status)
- Monthly performance charts
- Recent activity log
- Quick stats cards

**Sales View**:
- My Partners count
- My Leads (by status)
- Pending actions
- Recent leads activity
- Performance metrics

**RCU View**:
- Pending verifications
- Verified today
- Flagged partners
- Verification queue

### 3. Partner Management

#### Partner List
- Filterable table with columns:
  - Partner Code
  - Name
  - Type (DSA/Connector)
  - Branch
  - Tagged RM
  - Status (Active/Under Review/Rejected)
  - Leads Count
  - Disbursed Amount
  - Joined Date
- Search by name/code
- Filter by status, branch, type
- Export to CSV

#### Partner Details
- **Profile Section**:
  - Personal details (Name, Mobile, Email)
  - Partner type & code
  - Branch & RM details

- **KYC Section**:
  - Aadhaar status
  - PAN details
  - Address details
  - Business details (for Proprietor)
  - Bank account details

- **Documents Section**:
  - Uploaded documents list
  - Document verification status
  - RCU can verify/reject here

- **Performance Section**:
  - Total leads submitted
  - Conversion rate
  - Total disbursed
  - Commission earned

- **Leads Tab**:
  - List of all leads from this partner

### 4. Lead Management

#### Lead List
- Filterable table with columns:
  - Lead ID
  - Customer Name
  - Mobile
  - Loan Amount
  - Partner Name
  - Status
  - Created Date
  - Last Updated
- Search by name/mobile/ID
- Filter by status, date range, partner
- Bulk status update (Admin only)

#### Lead Details
- **Customer Info**:
  - Name, Mobile, Email
  - Loan requirement
  - Property details

- **Partner Info**:
  - Partner who submitted
  - Submission date

- **Status Timeline**:
  - Status history with timestamps
  - Comments log

- **Actions**:
  - Update status
  - Add comment
  - Assign to team member

### 5. User Management (Admin Only)

#### User List
- All portal users
- Role, Branch, Status
- Last login
- Add/Edit/Deactivate users

#### Add/Edit User
- Name, Email, Phone
- Role selection
- Branch assignment
- Partner tagging (for Sales)

### 6. Reports (Admin & Sales)
- Partner performance report
- Lead conversion report
- Branch-wise performance
- Monthly trends
- Export capabilities

---

## Status Definitions

### Partner Status
| Status | Description |
|--------|-------------|
| Profile Pending | Partner registered, profile incomplete |
| Under Review | Profile complete, pending verification |
| Active | Verified and active |
| Suspended | Temporarily suspended |
| Rejected | Application rejected |

### Lead Status
| Status | Description |
|--------|-------------|
| New | Just submitted |
| In Progress | Being processed |
| Documents Pending | Waiting for documents |
| Submitted to Bank | Sent for approval |
| Sanctioned | Loan approved |
| Disbursed | Loan disbursed |
| Rejected | Application rejected |

---

## Technical Notes

### Authentication
- Session-based authentication
- Role stored in session
- Auto-logout after inactivity

### Data Visibility
- Sales users see only tagged partners
- Admin sees all data
- RCU sees all partners for verification

### Audit Trail
- All actions logged
- User, timestamp, action recorded
- Viewable by Admin

---

## Color Scheme (Consistent with Partner App)

```css
--primary-dark: #1A5D38;
--primary: #228B4A;
--primary-light: #2FA55A;
--accent: #EDB41C;
--background: #F5F6F5;
--text-primary: #1A2E28;
--text-secondary: #6B7B75;
```

---

## Screen Flow

```
Login
  │
  ├─→ Dashboard (role-based)
  │     │
  │     ├─→ Partner List → Partner Details
  │     │
  │     ├─→ Lead List → Lead Details
  │     │
  │     ├─→ Reports (Admin/Sales)
  │     │
  │     └─→ User Management (Admin only)
  │
  └─→ Profile / Settings
```

---

## Files to Create

1. `index.html` - Master index
2. `Enterprise_Login.html` - Login screen
3. `Enterprise_Dashboard.html` - Admin dashboard
4. `Enterprise_Dashboard_Sales.html` - Sales dashboard
5. `Enterprise_Dashboard_RCU.html` - RCU dashboard
6. `Enterprise_Partners.html` - Partner list
7. `Enterprise_Partner_Details.html` - Partner details view
8. `Enterprise_Leads.html` - Lead list
9. `Enterprise_Lead_Details.html` - Lead details view
10. `Enterprise_Users.html` - User management (Admin)
