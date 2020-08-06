---
title: WMI 공급자에 프로그래밍 방식으로 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 67bd266b-1484-4863-8152-060a993420a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6546d046fcd176eb5cc5fd462ea9a8a31c25b803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652663"
---
# <a name="accessing-the-wmi-provider-programmatically"></a><span data-ttu-id="f868d-102">WMI공급자에 프로그래밍 방식으로 액세스</span><span class="sxs-lookup"><span data-stu-id="f868d-102">Accessing the WMI Provider Programmatically</span></span>
  <span data-ttu-id="f868d-103">[항목 작성 중]</span><span class="sxs-lookup"><span data-stu-id="f868d-103">This topic is under construction.</span></span>  
  
## <a name="wmi-provider-overview"></a><span data-ttu-id="f868d-104">WMI 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="f868d-104">WMI Provider Overview</span></span>  
 <span data-ttu-id="f868d-105">이 문서에 표시된 코드 예제의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]에 대한 정보를 얻는 데 사용되는 네임스페이스는 **System.Management** 네임스페이스이며 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f868d-105">The namespace used to obtain information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in the code samples shown in this topic is the **System.Management** namespace, found in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f868d-106">**System.Management** 네임스페이스는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 애플리케이션에서 관리 정보를 액세스하고 조작하는 데 사용할 수 있는 관리 코드 클래스 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f868d-106">The **System.Management** namespace provides a set of managed code classes through which [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] applications can access and manipulate management information.</span></span> <span data-ttu-id="f868d-107">**System.Management** 네임스페이스를 사용하여 Reporting Services WMI 클래스를 사용하는 방법은 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK의 “System.Management를 사용하여 관리 정보 액세스”를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f868d-107">For more information on using the Reporting Services WMI classes using the **System.Management** namespace, see "Accessing Management Information with System.Managment" in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="finding-a-report-server-instance"></a><span data-ttu-id="f868d-108">보고서 서버 인스턴스 찾기</span><span class="sxs-lookup"><span data-stu-id="f868d-108">Finding a Report Server Instance</span></span>  
 <span data-ttu-id="f868d-109">보고서 서버 설치에 대한 정보를 찾을 때는 WMI 인스턴스 컬렉션을 열거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f868d-109">The preferred way of finding information on your report server installations is to enumerate through the WMI instance collection.</span></span> <span data-ttu-id="f868d-110">아래 예는 컬렉션을 만들고 이 컬렉션을 반복하여 속성을 표시하는 방법으로 모든 보고서 서버 인스턴스에 대한 속성을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f868d-110">The example below shows how to find properties on every report server instance by creating a collection, and looping through the collection to display the properties.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports System.IO  
  
Module Module1  
    Sub Main()  
        Const WmiNamespace As String = "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin"  
        Const WmiRSClass As String = _  
           "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting"  
  
        Dim serverClass As ManagementClass  
        Dim scope As ManagementScope  
        scope = New ManagementScope(WmiNamespace)  
        'Connect to the Reporting Services namespace.  
        scope.Connect()  
  
        'Create the server class.  
        serverClass = New ManagementClass(WmiRSClass)  
        'Connect to the management object.  
        serverClass.Get()  
        If serverClass Is Nothing Then Throw New Exception("No class found")  
  
        'Loop through the instances of the server class.  
        Dim instances As ManagementObjectCollection = serverClass.GetInstances()  
        Dim instance As ManagementObject  
        For Each instance In instances  
            Console.Out.WriteLine("Instance Detected")  
            Dim instProps As PropertyDataCollection = instance.Properties  
            Dim prop As PropertyData  
            For Each prop In instProps  
                Dim name As String = prop.Name  
                Dim val As Object = prop.Value  
                Console.Out.Write("Property Name: " + name)  
                If val Is Nothing Then  
                    Console.Out.WriteLine("     Value: <null>")  
                Else  
                    Console.Out.WriteLine("     Value: " + val.ToString())  
                End If  
            Next  
        Next  
  
        Console.WriteLine("--- Press any key ---")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Management;  
using System.IO;  
[assembly: CLSCompliant(true)]  
  
class Class1  
{  
    [STAThread]  
    static void Main(string[] args)  
    {  
        const string WmiNamespace = @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin";  
        const string WmiRSClass =  
          @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\admin:MSReportServer_ConfigurationSetting";  
        ManagementClass serverClass;  
        ManagementScope scope;  
        scope = new ManagementScope(WmiNamespace);  
  
        // Connect to the Reporting Services namespace.  
        scope.Connect();  
        // Create the server class.  
        serverClass = new ManagementClass(WmiRSClass);  
        // Connect to the management object.  
        serverClass.Get();  
        if (serverClass == null)  
            throw new Exception("No class found");  
  
        // Loop through the instances of the server class.  
        ManagementObjectCollection instances = serverClass.GetInstances();  
  
        foreach (ManagementObject instance in instances)  
        {  
            Console.Out.WriteLine("Instance Detected");  
            PropertyDataCollection instProps = instance.Properties;  
            foreach (PropertyData prop in instProps)  
            {  
                string name = prop.Name;  
                object val = prop.Value;  
                Console.Out.Write("Property Name: " + name);  
                if (val != null)  
                    Console.Out.WriteLine("     Value: " + val.ToString());  
                else  
                    Console.Out.WriteLine("     Value: <null>");  
            }  
        }  
        Console.WriteLine("\n--- Press any key ---");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f868d-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f868d-111">See Also</span></span>  
 <span data-ttu-id="f868d-112">[Reporting Services WMI 공급자에 액세스](tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="f868d-112">[Access the Reporting Services WMI Provider](tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="f868d-113">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="f868d-113">RSReportServer Configuration File</span></span>](report-server/rsreportserver-config-configuration-file.md)  
  
  
