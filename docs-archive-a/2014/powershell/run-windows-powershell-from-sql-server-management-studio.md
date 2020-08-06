---
title: SQL Server Management Studio에서 Windows PowerShell 실행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0330e833aaa3344416a31aa700a2b1f6bb4a6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650147"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a><span data-ttu-id="e2a4b-102">SQL Server Management Studio에서 Windows PowerShell 실행</span><span class="sxs-lookup"><span data-stu-id="e2a4b-102">Run Windows PowerShell from SQL Server Management Studio</span></span>
  <span data-ttu-id="e2a4b-103">**의** 개체 탐색기 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 Windows PowerShell 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-103">You can start Windows PowerShell sessions from **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]<span data-ttu-id="e2a4b-104">Windows PowerShell을 시작 하 고 `sqlps` 모듈을 로드 한 다음 경로 컨텍스트를 **개체 탐색기** 트리의 연결 된 노드로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-104">launches Windows PowerShell, loads the `sqlps` module, and sets the path context to the associated node in the **Object Explorer** tree.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e2a4b-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e2a4b-105">Before You Begin</span></span>  
 <span data-ttu-id="e2a4b-106">**개체 탐색기**에서 개체에 대해 powershell을 실행 하도록 지정 하면에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] powershell 스냅인이 로드 및 등록 된 Windows powershell 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-106">When you specify running PowerShell for an object in **Object Explorer**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starts a Windows PowerShell session in which the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins have been loaded and registered.</span></span> <span data-ttu-id="e2a4b-107">세션 경로는 사용자가 개체 탐색기에서 마우스 오른쪽 단추로 클릭한 개체의 위치로 미리 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-107">The path for the session is preset to the location of the object you right clicked in Object Explorer.</span></span> <span data-ttu-id="e2a4b-108">예를 들어 개체 탐색기에서 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스 개체를 마우스 오른쪽 단추로 클릭하고 **PowerShell 시작**을 선택하면 Windows PowerShell 경로가 다음과 같이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-108">For example, if you right-click the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database object in Object Explorer and select **Start PowerShell**, the Windows PowerShell path is set to the following:</span></span>  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a><span data-ttu-id="e2a4b-109">SQL Server Management Studio에서 PowerShell을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="e2a4b-109">To run PowerShell from SQL Server Management Studio</span></span> 
  
1.  <span data-ttu-id="e2a4b-110">**개체 탐색기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-110">Open **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="e2a4b-111">작업할 개체에 대한 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-111">Navigate to the node for the object to be worked on.</span></span>  
  
3.  <span data-ttu-id="e2a4b-112">개체를 마우스 오른쪽 단추로 클릭하고 **PowerShell 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-112">Right-click the object and select **Start PowerShell**.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="e2a4b-113">사용 권한</span><span class="sxs-lookup"><span data-stu-id="e2a4b-113">Permissions</span></span>  
 <span data-ttu-id="e2a4b-114">PowerShell을 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에서 열 경우 관리자 권한으로 실행되지 않아 WMI에 대한 호출 등 일부 작업을 수행하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2a4b-114">When opened from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell does not run with Administrator privileges which may prevent some activities such as calls to WMI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a4b-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2a4b-115">See Also</span></span>  
 [<span data-ttu-id="e2a4b-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2a4b-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
