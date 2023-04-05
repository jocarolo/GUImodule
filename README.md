
# Powershell
# GUIModule_v1.0.psm1

## Project description

GUIModule_v1.0.psm1 is a first version of PowerShell module that provides functions for easily creating forms and graphical user interface (GUI) elements for PowerShell scripts. No need to use party tools, this module is 100% powershell and free, useful for those who want to create applications and tools based on PowerShell with a user-friendly graphical interface. We can use the GUIModule.psm1 module to create forms and buttons, text box, checkbox, etc..

You can use and customize the functions provided by the GUIModule.psm1 module to create a variety of GUI forms and elements to suit your specific requirements.

## Table of contents

1. [Prerequisites](#prerequsites)
2. [Installation](#installation)
3. [Use](#use)
4. [License](#license)
5. [Contact](#contact)

## Prerequisites

- PowerShell 5.1 or higher
- ActiveDirectory module for PowerShell (if used in an Active Directory environment)

## Installation

1. Download the GUIModule.psm1 file to your local computer.
2. Copy the GUIModule.psm1 file to one of the paths included in the $env:PSModulePath variable, for example, %USERPROFILE%\Documents\WindowsPowerShell\Modules\GUIModule.
3. Open a new PowerShell window and run the following command to import the module:

   ```
   Import-Module GUIModule
 
  ## Usage

Create a new form using the New-ScriptForm function.
Add controls to the form using the Add-* functions (e.g., Add-ScriptButton, Add-ScriptLabel, Add-ScriptTextBox, etc.).
Display the form using the Show-ScriptForm function.
Use the provided calculation functions to adjust the form's size, if needed.
Refer to the comments and examples within the GUIModule.psm1 script for more detailed usage instructions and examples.

```
Import-Module .\GUIModule.psm1

$form = New-ScriptForm -Title "Test modul" -Width 400 -Height 200

Add-ScriptLabel -Form $form -Text "Box1:" -Location (New-Object System.Drawing.Point(10, 20))
$usernameTextBox = Add-scriptTextBox -Form $form -Location (New-Object System.Drawing.Point(10, 50)) -Size (New-Object System.Drawing.Size(350, 20))

Add-scriptLabel -Form $form -Text "Box2:" -Location (New-Object System.Drawing.Point(10, 80))
$additionalInfoTextBox = Add-scriptTextBox -Form $form -Location (New-Object System.Drawing.Point(10, 110)) -Size (New-Object System.Drawing.Size(350, 20))

Add-scriptButton -Form $form -Text "Button1" -Location (New-Object System.Drawing.Point(10, 150)) -OnClick {
    Reset-UserPassword -Username $usernameTextBox.Text
}

Add-scriptButton -Form $form -Text "button2" -Location (New-Object System.Drawing.Point(110, 150)) -OnClick {
    $form.Close()
}

Add-ScriptCheckBox -Form $form -Text "Mi CheckBox" -Location (New-Object System.Drawing.Point(200, 150))

$groupBox = Add-ScriptGroupBox -Form $form -Text "Mi GroupBox" -Location (New-Object System.Drawing.Point(300, 150)) -Size (New-Object System.Drawing.Size(200, 100))

$radioButton1 = Add-ScriptRadioButton -Form $form -Text "Opción 1" -Location (New-Object System.Drawing.Point(200, 300))
$radioButton2 = Add-ScriptRadioButton -Form $form -Text "Opción 2" -Location (New-Object System.Drawing.Point(300, 300))

$groupBox = Add-ScriptGroupBox -Form $form -Text "Mi GroupBox" -Location (New-Object System.Drawing.Point(400, 300)) -Size (New-Object System.Drawing.Size(200, 100))
$radioButton3 = Add-ScriptRadioButton -Form $form -Text "Option 3" -Location (New-Object System.Drawing.Point(900, 300)) -GroupBox $groupBox
$radioButton4 = Add-ScriptRadioButton -Form $form -Text "Option 4" -Location (New-Object System.Drawing.Point(1000, 300)) -GroupBox $groupBox



$form.Size = Measure-scriptFormSize -Form $form

Show-scriptForm -Form $form
```

## License

This project is licensed under the MIT License.

## Contact

If you have any questions or suggestions, please feel free to open an issue on the project's GitHub repository (if available) or contact with me directly.
