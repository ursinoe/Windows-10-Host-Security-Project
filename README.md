<h1>Windows 10 Host Security Project</h1>

<h2>Objective</h2>
<p>The Windows 10 Host Security Project is designed to give you hands-on experience in securing Windows 10 hosts. You'll set up a secure Hyper-V lab, enable advanced security features, encrypt data, manage user permissions, and verify port security, all while learning essential Windows security practices.</p>

<h2>Skills Learned</h2>
<ul>
    <li>Setting up a secure Hyper-V lab environment.</li>
    <li>Enabling the Virtual Trusted Platform Module (TPM) and Virtualization-Based Security (VBS).</li>
    <li>Encrypting data using BitLocker.</li>
    <li>Managing file sharing and user permissions.</li>
    <li>Configuring port security with Windows Firewall.</li>
    <li>Securing Windows 10 systems effectively.</li>
</ul>

<h2>Tools Used</h2>
<ul>
    <li>Hyper-V for creating a secure lab environment.</li>
    <li>Virtual TPM and VBS tools.</li>
    <li>BitLocker for data encryption.</li>
    <li>Windows File Sharing and Permission Management tools.</li>
    <li>Windows Firewall for port security.</li>
</ul>

<h2>Steps</h2>

<h3>1. Set up a Secure Hyper-V Lab on Your Windows 10 Host</h3>
<ul>
    <li><strong>Reboot Your Computer:</strong> Enter BIOS/UEFI settings and enable virtualization (VTx). Restart your computer.</li>
    <li><strong>Install Hyper-V:</strong> Go to Control Panel &gt; Programs and Features &gt; Turn Windows features on or off &gt; Select all Hyper-V options. Reboot as needed.</li>
    <li><strong>Create a Virtual Machine:</strong> Use "Hyper-V Quick Create" to install a Windows 10 VM. If needed, follow this <a href="https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v">guide</a>.</li>
    <li><strong>Join a Domain:</strong> Add your VM to a domain, create a user named User1 with the password Passw0rd, and log in.</li>
    <li><strong>Rename Your Computer:</strong> Change the computer name to "Client". Follow this <a href="https://www.wikihow.com/Rename-Your-PC-in-Windows-10">guide</a>.</li>
    <li><strong>Install Windows Server 2019:</strong> Download an eval copy from <a href="https://www.microsoft.com/en-us/evalcenter/">Microsoft</a>. Create a second VM using the ISO file. Follow this <a href="https://youtu.be/r_UWOTFZ4os">video</a> if needed.</li>
    <li><strong>Configure IP Addresses:</strong>
        <ul>
            <li>Server: IP - 10.0.0.2, Subnet Mask - 255.255.255.0, DNS - 10.0.0.2.</li>
            <li>Client: IP - 10.0.0.1, Subnet Mask - 255.255.255.0, DNS - 10.0.0.2.</li>
        </ul>
    </li>
</ul>

<h3>2. Install and Configure Active Directory</h3>
<ul>
    <li><strong>Set Up Active Directory:</strong> Create a domain named test.internal. Add a user named Tom Terrific (password: Passw0rd) and a security group named Accounting. Add the Windows 10 client to the domain. Follow this <a href="https://youtu.be/6Lsv4N1hGnM">video</a>.</li>
    <li><strong>Verify Setup:</strong> Ensure both server and client appear in Active Directory Users and Computers.</li>
</ul>

<h3>3. Create and Configure Shared Folders</h3>
<ul>
    <li><strong>Create Shared Folder:</strong> On your server, create a folder named AcctClients. Configure share and security permissions to give Tom full access and Accounting group read and list access.</li>
    <li><strong>Check Effective Permissions:</strong> Verify Tom's effective permissions.</li>
</ul>

<h3>4. Hide Shares from Unauthorized Users</h3>
<ul>
    <li><strong>Create HR Group:</strong> Add only the administrator to the HR group. Create a share named HideMe, configure it for HR group only.</li>
    <li><strong>Verify Hidden Share:</strong> Log in as Tom on the client and ensure you can't see the share. Log in as Administrator to confirm visibility.</li>
</ul>

<h3>5. Encrypt a File with EFS</h3>
<ul>
    <li><strong>Encrypt Test File:</strong> Log in as Tom on the client, create and encrypt a test.txt file. Verify EFS certificate in personal certificates folder. Confirm encryption by seeing a lock on the file.</li>
</ul>

<h3>6. Enable BitLocker with vTPM</h3>
<ul>
    <li><strong>Add Partition:</strong> Create a 5 GB partition on your server. Add a test file.</li>
    <li><strong>Enable BitLocker:</strong> Turn on BitLocker for the new partition, save the recovery key as a PDF. Reboot and verify BitLocker encryption. Follow this <a href="https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan">guide</a> for BitLocker recovery.</li>
</ul>

<h3>7. Add and Secure IIS</h3>
<ul>
    <li><strong>Install IIS:</strong> Set up IIS on Server1. Access the default web page from the client.</li>
    <li><strong>Block Access by IP:</strong> Configure IIS to block access by client’s IP. Verify by trying to access the site.</li>
</ul>

<h3>8. Block by Firewall Port</h3>
<ul>
    <li><strong>Disable Port 80:</strong> In Windows Defender Firewall, disable port 80 (HTTP). Verify by trying to access the site from the client.</li>
</ul>

<h3>9. Secure IIS with a Certificate</h3>
<ul>
    <li><strong>Create Self-Signed Certificate:</strong> Use the wizard to create a certificate. Bind it to the default website. Access the site securely from the client.</li>
</ul>

</body>
</html>
