---
title: 구성 관리용 WMI 공급자에 WQL 및 스크립트 언어 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8c903cd0e993728865bce3371c349a2d0ba7485
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650837"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="6e125-102">구성 관리용 WMI 공급자에 WQL 및 스크립트 언어 사용</span><span class="sxs-lookup"><span data-stu-id="6e125-102">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="6e125-103">관리 애플리케이션에서는 다음과 같은 두 가지 방법으로 구성 관리용 WMI(Windows Management Instrumentation) 공급자 개체를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 네트워크 설정에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6e125-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings using the Windows Management Instrumentation (WMI) Provider for Configuration Management objects in two ways:</span></span>  
  
-   <span data-ttu-id="6e125-104">WQL 편집기 또는 WBEMTest.exe 같은 쿼리 도구를 사용하여 WQL(Windows Management Instrumentation Language)로 설정된 개체를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="6e125-104">Using a WQL editor or query tool, such as WBEMTest.exe to query the object set with the Windows Management Instrumentation Language (WQL).</span></span>  
  
-   <span data-ttu-id="6e125-105">VBScript 같은 스크립트 언어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e125-105">Using a scripting language, such as VBScript.</span></span>  
  
 <span data-ttu-id="6e125-106">또는 SMO에서 WMI 관리되는 개체를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 네트워크 설정을 프로그래밍 방식으로 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e125-106">Alternatively, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings can be managed programmatically using the WMI managed objects in SMO.</span></span> <span data-ttu-id="6e125-107">WMI 관리 개체를 프로그래밍 하는 방법에 대 한 자세한 내용은 [Wmi 공급자를 사용 하 여 서비스 및 네트워크 설정 관리](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e125-107">For more information about programming WMI managed objects, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="6e125-108">구성 관리용 WMI 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 관리 콘솔을 사용하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e125-108">The WMI provider for Configuration Management can be accessed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span> <span data-ttu-id="6e125-109">사용자 인터페이스에서 WMI 공급자에 액세스 하는 방법에 대 한 자세한 내용은 [서비스 관리 방법 도움말 항목 &#40;SQL Server 구성 관리자&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6e125-109">For more information about accessing the WMI provider from a user interface, see [Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e125-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e125-110">See Also</span></span>  
 <span data-ttu-id="6e125-111">[WQL을 사용 하 여 구성 관리용 WMI 공급자 액세스](access-wmi-provider-for-configuration-management-using-wql.md) </span><span class="sxs-lookup"><span data-stu-id="6e125-111">[Access WMI Provider for Configuration Management using WQL](access-wmi-provider-for-configuration-management-using-wql.md) </span></span>  
 [<span data-ttu-id="6e125-112">VBScript를 사용하여 SQL Server 서비스 고급 속성 수정</span><span class="sxs-lookup"><span data-stu-id="6e125-112">Modify SQL Server Service Advanced Properties using VBScript</span></span>](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
