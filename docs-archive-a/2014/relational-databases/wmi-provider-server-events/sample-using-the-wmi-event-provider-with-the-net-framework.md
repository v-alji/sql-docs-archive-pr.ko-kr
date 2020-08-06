---
title: '샘플: WMI 이벤트 공급자와 .NET Framework 사용 Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Server Events, samples
- sample applications [WMI]
- managed code [WMI]
ms.assetid: 3d7aa7e9-0bb3-4a5b-9a3c-047f3240a6f8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 42bd20750bef6fd388afb7b9a299b32b014ce351
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733684"
---
# <a name="sample-using-the-wmi-event-provider-with-the-net-framework"></a><span data-ttu-id="d871d-102">샘플: .NET Framework에서 WMI 이벤트 공급자 사용</span><span class="sxs-lookup"><span data-stu-id="d871d-102">Sample: Using the WMI Event Provider with the .NET Framework</span></span>
  <span data-ttu-id="d871d-103">다음 예에서는 WMI 이벤트 공급자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 설치 인스턴스에서 발생하는 모든 DDL 이벤트에 대한 이벤트 데이터를 반환하는 애플리케이션을 C#으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d871d-103">The following sample creates an application in C# that uses the WMI Event Provider to return event data for all data definition language (DDL) events that occur on a default installation instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="d871d-104">예제</span><span class="sxs-lookup"><span data-stu-id="d871d-104">Example</span></span>  
 <span data-ttu-id="d871d-105">이 예는 다음 명령 파일을 사용하여 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="d871d-105">The example compiles by using the following command file:</span></span>  
  
```  
set compiler_path=C:\WINNT\Microsoft.NET\Framework\v2.0.50110  
  
%compiler_path%\csc %1  
```  
  
```  
using System;  
using System.Management;  
  
class SQLWEPExample   
{  
    public static void Main(string[] args)  
    {  
        string query =  @"SELECT * FROM DDL_EVENTS " ;  
        // Default namespace for default instance of SQL Server   
        string managementPath =  
            @"\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER";  
        ManagementEventWatcher  watcher =   
            new ManagementEventWatcher(new WqlEventQuery (query));  
        ManagementScope scope = new ManagementScope (managementPath);  
        scope.Connect();  
        watcher.Scope = scope;  
        Console.WriteLine("Watching...");  
        while (true)  
        {  
            ManagementBaseObject obj = watcher.WaitForNextEvent();  
            Console.WriteLine("Event!");  
            foreach (PropertyData data in obj.Properties)  
            {  
                Console.Write("{0}:", data.Name);  
                if (data.Value == null)  
                {  
                    Console.WriteLine("<null>");  
                }  
                else  
                {  
                    Console.WriteLine(data.Value.ToString());  
                }  
            }  
            Console.WriteLine("-----");  
            Console.WriteLine();  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d871d-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d871d-106">See Also</span></span>  
 [<span data-ttu-id="d871d-107">서버 이벤트용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="d871d-107">WMI Provider for Server Events Concepts</span></span>](wmi-provider-for-server-events-concepts.md)  
  
  
