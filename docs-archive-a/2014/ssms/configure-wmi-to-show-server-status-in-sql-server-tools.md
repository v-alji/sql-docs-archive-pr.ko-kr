---
title: WMI를 구성하여 SQL Server 도구에 서버 상태 표시 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 138abbe2b7b819d6afd6da62135f7cd7ce86496f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737420"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a><span data-ttu-id="82447-102">WMI를 구성하여 SQL Server 도구에 서버 상태 표시</span><span class="sxs-lookup"><span data-stu-id="82447-102">Configure WMI to Show Server Status in SQL Server Tools</span></span>
  <span data-ttu-id="82447-103">이 항목에서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]의 SQL Server 도구에 서버 상태를 표시하기 위해 WMI를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-103">This topic describes how to configure WMI to show the server status in SQL Server tools in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="82447-104">서버에 연결할 때 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]구성 관리자와 함께 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 등록된 서버와 개체 탐색기 구성 요소는 WMI(Windows Management Instrumentation)를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스의 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82447-104">When connecting to servers, both the Registered Servers and Object Explorer components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], as well as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, use Windows Management Instrumentation (WMI) to obtain the status of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER) services.</span></span> <span data-ttu-id="82447-105">서비스의 상태를 표시하려면 사용자가 WMI 개체에 원격으로 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-105">To display the status of the service, the user must have rights to remotely access the WMI object.</span></span> <span data-ttu-id="82447-106">서버에는 이 사용 권한을 구성할 수 있도록 WMI가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-106">The server must have WMI installed to configure this permission.</span></span>  
  
##  <a name="to-configure-wmi-permission"></a><a name="SSMSProcedure"></a><span data-ttu-id="82447-107">WMI 사용 권한을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="82447-107">To configure WMI permission</span></span>  
  
1.  <span data-ttu-id="82447-108">원격 서버의 **시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-108">On the **Start** menu on the remote server, click **Run**.</span></span>  
  
2.  <span data-ttu-id="82447-109">**열기** 상자에를 입력 한 `wmimgmt.msc` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-109">In the **Open** box type `wmimgmt.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="82447-110">**Windows Management Infrastructure** 프로그램에서 **WMI 컨트롤(로컬)** 을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-110">In the **Windows Management Infrastructure** program, right-click **WMI Control (Local)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="82447-111">**WMI 컨트롤(로컬) 속성** 대화 상자의 **보안** 탭에서 **루트**를 확장한 다음 **CIMV2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-111">In the **WMI Control (Local) Properties** dialog box, on the **Security** tab, expand **Root**, and then click **CIMV2**.</span></span>  
  
5.  <span data-ttu-id="82447-112">**보안** 을 클릭하여 **ROOT\CIMV2 보안** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82447-112">Click **Security** to open the **Security for ROOT\CIMV2** dialog box.</span></span>  
  
6.  <span data-ttu-id="82447-113">**그룹 또는 사용자 이름** 상자에 그룹 또는 사용자를 추가하고 해당 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-113">Add a group or user to the **Group or user names** box and select it.</span></span>  
  
7.  <span data-ttu-id="82447-114">**에 대한 사용 권한** _\<group or user>_ 상자에서 서비스 상태를 원격으로 검색하려는 사용자의 경우 **원격으로부터 사용 가능** 사용 권한에 대해 **허용** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82447-114">In the **Permissions for**_\<group or user>_ box, select the **Allow** column, for the **Remote Enable** permission, for users whom you wish to remotely detect the service status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82447-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82447-115">See Also</span></span>  
 [<span data-ttu-id="82447-116">SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지</span><span class="sxs-lookup"><span data-stu-id="82447-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
