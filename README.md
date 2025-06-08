# Interop
<h4>Simply an implementation of https://www.pinvoke.net</h4>

# What is Platform Invoke (P/Invoke) ?
P/Invoke is a technology that allows you to access structs, callbacks, and functions in unmanaged libraries from your managed code. Most of the P/Invoke API is contained in two namespaces: System and System.Runtime.InteropServices. Using these two namespaces give you the tools to describe how you want to communicate with the native component.

# Example
```cs
using System;
using System.Runtime.InteropServices;

public partial class Program
{
    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [LibraryImport("user32.dll", StringMarshalling = StringMarshalling.Utf16, SetLastError = true)]
    private static partial int MessageBoxW(IntPtr hWnd, string lpText, string lpCaption, uint uType);

    public static void Main(string[] args)
    {
        // Invoke the function as a regular managed method.
        MessageBoxW(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```
