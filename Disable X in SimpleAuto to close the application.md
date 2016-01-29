# **Disable X in SimpleAuto to close the application** #

## **Question / Description** ##

We are experimenting a rare behavior in SimpleAuto stations, when the operator clicks the “X” in the upper right corner of the GUI the efSimpleAuto.exe hangs and remains running as orphan.  If the operator choose the option “File” and then “Exit”, the efSimpleAuto.exe close normally.
 
So, any of you knows how to disable the option to close the application using the “X”?


## **Answer / Solution** ##

Paste the class below anywhere in your code,
in the OnLogin event of the stations to disable the close button call the following:

DisableWindowSystemMenu.DisableSystemMenu(csm);

![](http://i.imgur.com/1iAUxkU.jpg)

This is how the simple auto station window will look (in this case with no application name as ApplicationId command parameter was not specified).
 
 
using System;
using System.Collections.Generic;
using System.Runtime.InteropServices;
using System.Text;
using TiS.Core.eFlowAPI;
 
namespace YOUR_Namespace
{
  #region "DisableWindowSystemMenu" class
    public class DisableWindowSystemMenu
    {
        #region Windows API calls
        [DllImport("user32.dll", EntryPoint = "FindWindow")]
        private static extern IntPtr FindWindow(string sClass, string sWindow);
 
        [DllImport("User32.dll")]
        private static extern int SetWindowLong(IntPtr hWnd, int nIndex, int dwNewLong);
 
        [DllImport("User32.dll")]
        private static extern int GetWindowLong(IntPtr hWnd, int nIndex);
        #endregion
 
        #region Windows APIs constants
        private const int GWL_STYLE = -16;
        private const int WS_SYSMENU = 0x00080000; //window menu   
        #endregion
 
        #region "DisableSystemMenu" function
        /// <summary>
        /// Diable the station window's system menu.
        /// </summary>
        /// <param name="csm"></param>
        /// <returns>true when successful.</returns>
        public static bool DisableSystemMenu(ITisClientServicesModule csm)
        {
            try
            {
                //-- Find the current station window, have to use the window title for that --\\
                IntPtr ptr = FindWindow(null, string.Format("{0} - {1}", csm.Setup.Name, csm.Session.StationName));
 
                //-- In case this is the default application and no ApplicationId specified --\\
                if (ptr == IntPtr.Zero) ptr = FindWindow(null, string.Format(" - {0}", csm.Session.StationName));
 
                if (ptr != IntPtr.Zero)
                {
                    //-- Get the current window style --\\
                    int style = GetWindowLong(ptr, GWL_STYLE);
 
                    //-- Remove the system menu and the close button --\\
                    SetWindowLong(ptr, GWL_STYLE, style & ~WS_SYSMENU);
 
                    return style != 0;
                }
            }
            catch (Exception ex)
            {
                ILog.LogError(ex);
            }
            return false;
        }
        #endregion
    } 
    #endregion 
}



















