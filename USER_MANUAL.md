# ESN Buddy Program - User Manual

## Table of Contents
1. [Introduction](#introduction)
2. [User Roles and Permissions](#user-roles-and-permissions)
3. [Getting Started](#getting-started)
4. [Navigation & User Interface](#navigation--user-interface)
5. [Registration Process](#registration-process)
6. [Authentication & Login](#authentication--login)
7. [Admin Functions](#admin-functions)
8. [Matching System](#matching-system)
9. [Data Export & Management](#data-export--management)
10. [Email Notifications](#email-notifications)
11. [Error Handling & Common Issues](#error-handling--common-issues)
12. [Best Practices & Warnings](#best-practices--warnings)
13. [Glossary](#glossary)

---

## 1. Introduction

### What is the ESN Buddy Program?
The **ESN Buddy Program** is a web-based application designed to facilitate the matching of international students (Buddies) with local ESN members (ESNers) in Palermo. The system helps incoming exchange students integrate smoothly by connecting them with experienced local students who share similar interests, languages, and academic backgrounds.

### Main Purpose
- **Connect international students with local mentors**
- **Facilitate cultural integration and academic support**
- **Streamline the administrative process of buddy assignments**
- **Provide comprehensive data management for ESN administrators**

### Key Features
✅ **Automated Matching System** - Intelligent pairing based on compatibility factors  
✅ **Role-Based Access Control** - Different permissions for admins, managers, and users  
✅ **Registration Management** - Separate registration flows for Buddies and ESNers  
✅ **Data Export** - Excel export functionality for administrative purposes  
✅ **Email Notifications** - Automated notifications for registrations and matches  
✅ **Multi-language Support** - Interface supporting multiple languages  

---

## 2. User Roles and Permissions

### 2.1 Buddy (Exchange Student)
**Who they are:** International students coming to Palermo for exchange programs.

**Capabilities:**
- Register through the buddy registration form
- Provide personal information, interests, and preferences
- Receive match notifications via email
- No login access to the system

**Restrictions:**
- Cannot access administrative functions
- Cannot view other users' information
- Cannot modify their information after registration

### 2.2 ESNer (ESN Member/Mentor)
**Who they are:** Local ESN Palermo members who mentor exchange students.

**Capabilities:**
- Register through the ESNer registration form
- Log into their profile
- Update their profile information
- View their assigned buddies
- Set their availability (max number of buddies)

**Login Requirements:**
- Must use official ESN Palermo email (@esn...)
- Password-protected account access

### 2.3 Buddy Program Manager
**Who they are:** ESN members responsible for managing the buddy program.

**Capabilities:**
- All ESNer capabilities
- Access matching interfaces (manual and automatic)
- Confirm and remove matches
- View all registered users
- Remove individual buddies from the system

**Special Access:**
- Manual matching interface at `/match/manual_match`
- Automatic matching interface at `/match/automatic_match`

### 2.4 Buddy Program Admin
**Who they are:** Senior ESN members with enhanced administrative privileges.

**Capabilities:**
- All Buddy Program Manager capabilities
- Export all data to Excel
- Remove all data from the system (after export)
- Remove individual ESNers (if they have no assigned buddies)

**Critical Functions:**
- System-wide data management
- GDPR compliance operations

### 2.5 System Admin
**Who they are:** Technical administrators with full system access.

**Capabilities:**
- All previous role capabilities
- Manage user roles and permissions
- Add/remove other admins and managers
- View detailed user profiles
- Toggle user active/inactive status
- Access admin dashboard at `/admin/index`

**Super User Privileges:**
- Cannot be deleted by other admins
- Full system configuration access

---

## 3. Getting Started

### 3.1 System Access
- **Main URL:** The application is accessed through its web interface
- **Home Page:** Automatically redirects to login page for authenticated access
- **Public Pages:** Registration forms are publicly accessible

### 3.2 First Time Users

**For Buddies (Exchange Students):**
1. Navigate to `/buddy/registration`
2. Complete the registration form with all required information
3. Wait for email confirmation
4. Await matching notification from ESN team

**For ESNers (ESN Members):**
1. Navigate to `/esner/registration`  
2. Complete registration using official ESN Palermo email
3. Create a secure password
4. Wait for approval from administrators
5. Log in using your credentials at `/auth/login`

---

## 4. Navigation & User Interface

### 4.1 Public Pages

**Registration Pages:**
- `/buddy/registration` - Exchange student registration
- `/esner/registration` - ESN member registration
- `/TermAndCondition` - Terms and conditions

**Authentication Pages:**
- `/auth/login` - Login page for ESNers
- `/auth/forgot_password` - Password recovery
- `/auth/reset_password` - Password reset with token

### 4.2 Authenticated User Pages

**ESNer Dashboard:**
- `/esner/profile` - View personal profile and assigned buddies
- `/esner/update_profile` - Update personal information

**Admin Areas:**
- `/admin/index` - Admin dashboard with all ESNers
- `/admin/esner/{id}` - Individual ESNer management

**Matching System:**
- `/match/manual_match` - Manual buddy-ESNer pairing
- `/match/automatic_match` - AI-powered automatic matching

### 4.3 Navigation Patterns
- **Breadcrumbs:** Clear navigation hierarchy
- **Role-based menus:** Different options based on user permissions
- **Responsive design:** Works on desktop and mobile devices

---

## 5. Registration Process

### 5.1 Buddy Registration

**Step 1: Access Registration Form**
- Navigate to `/buddy/registration`
- Form loads with available options for all dropdown fields

**Step 2: Required Information**
- **Personal Details:** Name, surname, email, phone number
- **Social Media:** Instagram handle, Telegram username
- **Academic Info:** Faculty, semester (Fall/Spring), year
- **Personal Preferences:** Nationality, languages spoken, interests
- **Additional Info:** Gender, description (optional)

**Step 3: Form Validation**
- Email must be unique (not already registered)
- Phone number must be unique
- All required fields must be completed

**Step 4: Submission Process**
- Form data is validated on client and server side
- Confirmation email is sent automatically
- Registration is stored in the database

**Step 5: After Registration**
- Buddy receives confirmation email
- Profile enters the matching pool
- No further action required from buddy

### 5.2 ESNer Registration

**Step 1: Access Registration Form**
- Navigate to `/esner/registration`
- Must use official ESN Palermo email address

**Step 2: Required Information**
- **Personal Details:** Name, surname, official ESN email, phone
- **ESN Role:** Type (Volunteer, Honorarium, Alumnus)
- **Capacity:** Maximum number of buddies they can mentor
- **Preferences:** Languages, nationality, faculty, interests
- **Security:** Strong password for account access

**Step 3: Email Validation**
- Email must contain "esn" in domain name
- Email and phone must be unique in the system
- Password is securely hashed before storage

**Step 4: Account Creation**
- ESNer account is created with login capabilities
- Profile is set as active by default
- Can immediately log in after successful registration

---

## 6. Authentication & Login

### 6.1 Login Process

**Accessing the Login Page:**
- Navigate to `/auth/login` or click login link
- Root URL (`/`) automatically redirects to login

**Login Requirements:**
- Valid ESN Palermo email address
- Correct password

**Step-by-Step Login:**
1. Enter your registered email address
2. Enter your password
3. Click submit or press Enter
4. System validates credentials
5. Successful login redirects to your profile page

### 6.2 Password Recovery

**If You Forgot Your Password:**
1. Go to `/auth/forgot_password`
2. Enter your registered email address
3. Check your email for reset link
4. Click the reset link (valid for 24 hours)
5. Enter your new password twice to confirm
6. Submit the new password
7. Log in with your new credentials

**Password Reset Security:**
- Reset tokens expire after 24 hours
- Tokens can only be used once
- Old tokens are automatically invalidated
- IP address and browser information are logged

### 6.3 Session Management

**Session Features:**
- Sessions persist across browser sessions
- Automatic logout after extended inactivity
- Secure session handling prevents unauthorized access

**Logging Out:**
- Click logout link in navigation
- Or navigate to `/auth/logout`
- Session is completely cleared
- Redirects to login page

---

## 7. Admin Functions

### 7.1 Admin Dashboard (`/admin/index`)

**Overview Display:**
- List of all registered ESNers
- Role information for each ESNer
- Quick access to individual ESNer profiles
- Active/inactive status indicators

**Available Actions:**
- View individual ESNer details
- Edit ESNer information
- Manage roles and permissions
- Toggle active/inactive status

### 7.2 ESNer Management (`/admin/esner/{id}`)

**Profile Information:**
- Complete ESNer profile details
- Current role assignments
- List of assigned buddies
- Contact and personal information

**Edit Capabilities:**
- Update personal information (name, surname, phone, email)
- Change password (if provided)
- Modify role assignments
- Set active/inactive status

**Deletion Rules:**
- ESNers can only be deleted if they have no assigned buddies
- Admins cannot delete themselves
- Data elimination email is sent when deleting an ESNer
- At least one admin must remain in the system

### 7.3 Role Management (`/admin/esner/{id}/role`)

**Adding Roles:**
- Select from available roles (Admin, Buddy Program Admin, Buddy Program Manager)
- Prevents duplicate role assignments
- Immediate effect upon assignment

**Removing Roles:**
- Cannot remove the only admin role from the system
- System checks ensure at least one admin remains
- Immediate effect upon removal

**Available Roles:**
- **Admin:** Full system access
- **Buddy Program Admin:** Enhanced program management
- **Buddy Program Manager:** Basic program management

### 7.4 Bulk Operations (`/admin/export_and_remove_all`)

**Export and Delete All Data:**
- **Purpose:** GDPR compliance and semester cleanup
- **Process:** 
  1. Export all buddy and ESNer data to Excel
  2. Delete all buddy records
  3. Delete ESNers without roles
  4. Preserve admin accounts
- **Warning:** This action is irreversible
- **Access:** Only Buddy Program Admins can perform this operation

### 7.5 ESNer Verification (`/admin/check_esner`)

**Name Verification Tool:**
- Upload lists of names and surnames
- Compare against registered ESNers in database
- Identify unregistered individuals
- Uses fuzzy matching for name variations
- Returns detailed report of matches/mismatches

---

## 8. Matching System

### 8.1 Understanding the Matching Algorithm

**Compatibility Factors:**
- **Languages Spoken** (highest weight) - Shared communication languages
- **Shared Interests** - Common hobbies and activities  
- **Faculty** - Academic field similarity
- **Gender Preferences** - Matching preferences when specified
- **Nationality** - Cultural connection opportunities

**Matching Score:**
- Each factor contributes to an overall compatibility score
- Higher scores indicate better potential matches
- System balances availability with compatibility

### 8.2 Automatic Matching (`/match/automatic_match`)

**How It Works:**
1. System identifies ESNers with available buddy slots
2. Finds unmatched buddies in the system
3. Calculates compatibility scores for all possible pairs
4. Selects optimal matches to maximize overall satisfaction
5. Presents recommended matches for approval

**Prerequisites:**
- Must have available ESNers (not at maximum buddy capacity)
- Must have unmatched buddies
- ESNers must be active in the system

**Review Process:**
- System shows recommended matches with compatibility scores
- Administrators can approve or reject suggestions
- Manual adjustments can be made before confirmation

### 8.3 Manual Matching (`/match/manual_match`)

**Interface Features:**
- **ESNer List:** Ordered by current buddy count (least busy first)
- **Buddy List:** Ordered by match status and registration date
- **Visual Indicators:** Clear status indicators for matched/unmatched
- **Quick Actions:** Direct match/unmatch buttons

**Manual Matching Process:**
1. Review available ESNers and their current buddy count
2. Select a buddy from the unmatched list
3. Choose an appropriate ESNer for pairing
4. Click "Match" to create the assignment
5. System sends confirmation emails to both parties

### 8.4 Match Confirmation (`/match/confirm_match`)

**Confirmation Process:**
1. Buddy is assigned to the selected ESNer
2. Email notifications are sent to both parties
3. Database is updated with the new relationship
4. Match appears in both users' profiles

**Email Notifications Include:**
- **For Buddies:** Welcome message, ESNer contact information, next steps
- **For ESNers:** New buddy assignment, buddy details, coordination instructions

### 8.5 Match Removal (`/match/remove_match`)

**When to Remove Matches:**
- Buddy cancels their exchange program
- ESNer becomes unavailable
- Personality conflicts require reassignment
- Academic schedule changes

**Removal Process:**
1. Select the matched buddy for removal
2. Confirm the unmatch operation
3. System sends notification emails to both parties
4. Buddy becomes available for re-matching
5. ESNer slot becomes available for new assignments

---

## 9. Data Export & Management

### 9.1 Excel Export (`/match/export_excel`)

**Export Contents:**
- **Buddies Sheet:** Complete buddy information including personal details, preferences, and match status
- **ESNers Sheet:** Complete ESNer information including capacity and assigned buddies

**Excel File Structure:**
- Professional formatting with clear headers
- Separate worksheets for different data types
- Date formatting for timestamps
- JSON data converted to readable format

**Use Cases:**
- Semester reporting
- ESN network reporting  
- Backup for data security
- Analysis and statistics

### 9.2 Complete System Reset (`/admin/export_and_remove_all`)

**Purpose:**
- End-of-semester cleanup
- GDPR compliance
- Fresh start for new academic periods

**Process:**
1. **Export Phase:** All data exported to Excel file
2. **Deletion Phase:** 
   - All buddy records deleted
   - ESNers without administrative roles deleted  
   - Admin accounts preserved for continuity
3. **Download:** Exported file automatically downloaded

**Data Preservation:**
- Administrative accounts remain intact
- System roles and permissions preserved
- Configuration settings maintained

### 9.3 Individual Data Removal

**Buddy Removal (`/match/remove/buddy/{id}`):**
- Deletes specific buddy record
- Sends data elimination notification email
- Frees up associated ESNer slot if matched
- Immediate and permanent deletion

**ESNer Removal Restrictions:**
- Can only delete ESNers with no assigned buddies
- Must first remove or reassign all their buddies
- Cannot delete yourself as an admin
- System prevents deletion of the last admin

---

## 10. Email Notifications

### 10.1 Registration Confirmations

**Buddy Registration Email:**
- Sent immediately upon successful registration
- Confirms registration details
- Provides information about next steps
- Includes ESN contact information

**ESNer Registration:**
- Currently no automatic email (administrative decision)
- ESNers can immediately log in after registration

### 10.2 Matching Notifications

**Buddy Match Notification:**
- Sent when assigned to an ESNer
- Includes ESNer contact information
- Provides guidance on first contact
- Contains useful tips for the buddy program experience

**ESNer Match Notification:**
- Sent when a new buddy is assigned
- Includes buddy contact and preference information
- Contains mentorship guidance
- Provides program coordination instructions

### 10.3 System Notifications

**Unmatch Notifications:**
- Sent to both parties when a match is removed
- Explains the reason for unmatch (if provided)
- For buddies: information about potential re-matching
- For ESNers: notice of slot availability

**Data Elimination Notices:**
- Sent when user data is deleted from system
- GDPR compliance notification
- Explains data retention policies
- Provides contact information for questions

**Password Reset Emails:**
- Secure reset links with 24-hour expiration
- Clear instructions for password reset process
- Security information and best practices

---

## 11. Error Handling & Common Issues

### 11.1 Registration Errors

**"Email already registered" Error:**
- **Cause:** Attempting to register with an email already in the system
- **Solution:** Use a different email address or contact administrators if you believe this is an error
- **For ESNers:** Ensure you're using your official ESN Palermo email

**"Phone number already registered" Error:**
- **Cause:** Phone number is already associated with another user
- **Solution:** Verify your phone number or use an alternative number
- **Note:** Each user must have a unique phone number

**"Email must be the official one" (ESNer registration):**
- **Cause:** Email doesn't contain "esn" in the domain
- **Solution:** Use your official ESN Palermo email address (@esn...)
- **Contact:** Reach out to ESN administrators if you don't have an official email

### 11.2 Login Issues

**"Invalid credentials" Error:**
- **Cause:** Incorrect email or password
- **Solutions:**
  1. Verify email address (must be the same used for registration)
  2. Check password spelling and capitalization
  3. Use password reset if you've forgotten your password
  4. Contact administrators if problem persists

**Redirect to Login After Logout:**
- **Behavior:** Normal system behavior
- **Cause:** Session has been cleared for security
- **Solution:** Log in again with your credentials

### 11.3 Matching Errors

**"Not enough data for auto-matching" Error:**
- **Cause:** Insufficient buddies or ESNers with available capacity
- **Solutions:**
  1. Wait for more registrations
  2. Check ESNer capacity settings
  3. Verify ESNer active status
  4. Use manual matching instead

**"Buddy or ESNer not found" (during matching):**
- **Cause:** Selected user doesn't exist in database
- **Solution:** Refresh the page and try again
- **Contact:** Report persistent issues to administrators

### 11.4 Permission Errors

**403 Forbidden Errors:**
- **Cause:** Attempting to access functions above your permission level
- **Solution:** Contact administrators for role clarification or elevation
- **Common scenarios:** 
  - Managers trying to access admin-only functions
  - Non-admins trying to delete users

**404 Page Not Found:**
- **Cause:** URL doesn't exist or has been mistyped
- **Solution:** Check URL spelling and try again
- **Navigation:** Use the provided navigation menus instead of direct URLs

---

## 12. Best Practices & Warnings

### 12.1 Data Management Best Practices

**Regular Exports:**
- Export data regularly for backup purposes
- Keep exported files secure and GDPR-compliant
- Use exports for reporting and analysis

**User Information Updates:**
- ESNers should keep their profiles current
- Update capacity when availability changes
- Notify administrators of extended absences

**Match Management:**
- Confirm matches promptly to avoid confusion
- Remove matches only when necessary
- Communicate changes to affected users

### 12.2 Security Best Practices

**Password Security:**
- Use strong, unique passwords
- Don't share login credentials
- Use password reset feature if password is compromised
- Log out when using shared computers

**Account Security:**
- Don't leave sessions unattended
- Report suspicious activity immediately
- Keep contact information current

### 12.3 Administrative Warnings

**⚠️ CRITICAL: Export and Delete All Data**
- **This action is IRREVERSIBLE**
- **Always export data before deletion**
- **Confirm you have the exported file before proceeding**
- **Only perform at end of semester or for GDPR compliance**

**⚠️ IMPORTANT: Role Management**
- **Never remove the last admin from the system**
- **Be cautious when modifying your own permissions** 
- **Verify role changes before confirming**

**⚠️ WARNING: User Deletion**
- **ESNer deletion is permanent**
- **Cannot delete ESNers with assigned buddies**
- **Data elimination emails are sent automatically**
- **Consider deactivating instead of deleting**

### 12.4 GDPR Compliance

**Data Retention:**
- Personal data is kept only as long as necessary
- Users can request data deletion
- System provides tools for bulk data removal
- Notification emails are sent for data elimination

**User Rights:**
- Users have the right to access their data
- Users can request corrections to their information
- Data export functionality supports data portability
- Contact administrators for data-related requests

---

## 13. Glossary

**Buddy**
- An exchange student participating in the ESN Buddy Program
- International student coming to Palermo for studies
- Receives support and mentorship from ESNers

**ESNer** 
- An ESN (Erasmus Student Network) member
- Local student who mentors exchange students
- Has login access to the system and can manage their profile

**ESN Palermo**
- Local section of the Erasmus Student Network in Palermo
- Organization managing the buddy program
- Official email addresses contain "esn" in the domain

**Matching**
- Process of pairing buddies with ESNers
- Can be automatic (algorithm-based) or manual (administrator-selected)
- Based on compatibility factors like languages, interests, and faculty

**Buddy Program Admin**
- Senior ESN member with enhanced administrative privileges
- Can export data and perform system-wide operations
- Has access to all buddy program management functions

**Buddy Program Manager**
- ESN member responsible for day-to-day buddy program operations  
- Can create and manage matches between buddies and ESNers
- Has access to matching interfaces and user management

**System Admin**
- Technical administrator with full system access
- Can manage user roles and system configuration
- Has the highest level of permissions in the system

**Compatibility Score**
- Numerical rating of how well a buddy and ESNer match
- Calculated based on shared languages, interests, faculty, and other factors
- Used by the automatic matching algorithm to suggest optimal pairings

**Active/Inactive Status**
- Indicates whether an ESNer is currently available for matches
- Inactive ESNers are excluded from the matching process
- Can be toggled by administrators

**Capacity**
- Maximum number of buddies an ESNer can mentor simultaneously
- Set during registration and can be updated in profile
- Used to determine ESNer availability for new matches

**GDPR Compliance**
- Adherence to General Data Protection Regulation
- Includes data export, deletion, and user notification features
- System provides tools for data management and user rights

**JSON Fields**
- Database fields that store multiple values (like languages or interests)
- Displayed as user-friendly lists in the interface
- Allow flexible storage of varying amounts of data

**Session Management**
- System for maintaining user login state
- Handles authentication and permission checking
- Automatically logs out inactive users for security

---

## Support and Contact Information

For technical issues, questions, or support:
- **Email:** giorgiodicristofalo77@gmail.com
- **GitHub Issues:** Report bugs and feature requests through the project repository
- **ESN Palermo Contact:** Reach out through official ESN channels for program-related questions

---

*This manual covers version 1.0 of the ESN Buddy Program system. Please refer to the latest documentation for updates and new features.*