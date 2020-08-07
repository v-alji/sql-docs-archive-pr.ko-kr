---
title: Analysis Services 서버에서 사용자와 세션 연결 끊기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: bac20b663b0a65902c70e7a3c3bfe3f27b7bf061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731068"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a><span data-ttu-id="b8b0e-102">Analysis Services 서버에서 사용자와 세션 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="b8b0e-102">Disconnect Users and Sessions on Analysis Services Server</span></span>
  <span data-ttu-id="b8b0e-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 관리자는 작업 관리 중에 사용자 작업을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-103">An administrator of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] may want to end user activity as part of workload management.</span></span> <span data-ttu-id="b8b0e-104">사용자 작업을 종료하려면 세션 및 연결을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-104">You do this by canceling sessions and connections.</span></span> <span data-ttu-id="b8b0e-105">세션은 쿼리 실행 시(암시적) 또는 관리자가 쿼리 생성 시 이름을 지정하면(명시적) 자동으로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-105">Sessions can be formed automatically when a query is run (implicit), or named at the time of creation by the administrator (explicit).</span></span> <span data-ttu-id="b8b0e-106">연결은 쿼리를 실행할 수 있는 열린 통로입니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-106">Connections are open conduits over which queries can be run.</span></span> <span data-ttu-id="b8b0e-107">세션과 연결 모두 활성 상태에서 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-107">Both sessions and connections can be ended while they are active.</span></span> <span data-ttu-id="b8b0e-108">예를 들어 관리자는 처리 시간이 너무 오래 걸리거나 실행 중인 명령이 올바르게 작성되었다는 확신이 없을 경우 세션 처리를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-108">For example, an administrator may want to end processing for a session if the processing is taking too long or if some doubt has arisen as to whether the command being executed was written correctly.</span></span>  
  
## <a name="ending-sessions-and-connections"></a><span data-ttu-id="b8b0e-109">세션 및 연결 종료</span><span class="sxs-lookup"><span data-stu-id="b8b0e-109">Ending Sessions and Connections</span></span>  
 <span data-ttu-id="b8b0e-110">DMV(동적 관리 뷰) 및 XMLA를 사용하여 세션 및 연결을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-110">To manage sessions and connections, you can use Dynamic Management Views (DMVs) and XMLA:</span></span>  
  
1.  <span data-ttu-id="b8b0e-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 Analysis Services 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-111">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="b8b0e-112">MDX 쿼리 창에 다음 DMV 쿼리 중 하나를 붙여넣어 현재 실행 중인 모든 세션, 연결 및 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-112">Paste any one of the following DMV queries in an MDX query window to get a list of all sessions, connections, and commands that are currently executing:</span></span>  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  <span data-ttu-id="b8b0e-113">F5 키를 눌러 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-113">Press F5 to execute the query.</span></span>  
  
     <span data-ttu-id="b8b0e-114">DMV 쿼리는 읽고 복사하기 쉬운 테이블 형식의 결과 집합으로 세션 및 연결 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-114">The DMV query returns session and connection information in a tabular result set that is easier read and copy from.</span></span>  
  
 <span data-ttu-id="b8b0e-115">쿼리 창을 계속 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-115">Keep the query window open.</span></span> <span data-ttu-id="b8b0e-116">다음 단계에서 이 페이지로 돌아와 연결을 끊으려는 세션의 SPID를 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-116">In the next step, you will want to return to this page to copy the SPIDs of the session you want to disconnect.</span></span>  
  
 <span data-ttu-id="b8b0e-117">세션을 종료하려면 두 번째 XMLA 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-117">To end a session, open a second XMLA query window.</span></span>  
  
1.  <span data-ttu-id="b8b0e-118">MDX 쿼리 창에 다음 구문을 붙여넣고 ConnectionID, SessionID 또는 SPID 자리 표시자를 이전 단계에서 복사한 올바른 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-118">Paste the following syntax into an MDX query window, replacing the ConnectionID, SessionID, or SPID placeholder with a valid value copied from the previous step.</span></span>  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  <span data-ttu-id="b8b0e-119">F5 키를 눌러 취소 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-119">Press F5 to execute the cancel command.</span></span>  
  
 <span data-ttu-id="b8b0e-120">연결을 종료하면 호스트 세션이 닫히면서 모든 세션과 SPID가 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-120">Ending a connection cancels all sessions and SPIDs, closing the host session.</span></span>  
  
 <span data-ttu-id="b8b0e-121">세션을 종료하면 해당 세션의 일부로 실행 중인 모든 명령(SPID)이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-121">Ending a session stops all commands (SPIDs) that are running as part of that session.</span></span>  
  
 <span data-ttu-id="b8b0e-122">SPID를 종료하면 특정 명령이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-122">Ending a SPID cancels a particular commend.</span></span>  
  
 <span data-ttu-id="b8b0e-123">아주 드물게는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 연결과 관련된 모든 세션 및 SPID를 추적할 수 없는 경우(예: HTTP 시나리오에서 여러 개의 세션이 열려 있는 경우) 이 연결을 닫지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-123">In rare cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will not close a connection if it cannot track all the sessions and SPIDs associated with the connection (for example, when multiple sessions are open in an HTTP scenario).</span></span>  
  
 <span data-ttu-id="b8b0e-124">이 항목에서 참조하는 XMLA에 대한 자세한 내용은 [Execute 메서드&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 및 [Cancel 요소&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8b0e-124">For more information about the XMLA referenced in this topic, see [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) and [Cancel Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b0e-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8b0e-125">See Also</span></span>  
 <span data-ttu-id="b8b0e-126">[XMLA&#41;&#40;연결 및 세션 관리](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="b8b0e-126">[Managing Connections and Sessions &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md) </span></span>  
 <span data-ttu-id="b8b0e-127">[XMLA 세션 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="b8b0e-127">[BeginSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla) </span></span>  
 <span data-ttu-id="b8b0e-128">[EndSession 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="b8b0e-128">[EndSession Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla) </span></span>  
 [<span data-ttu-id="b8b0e-129">Session 요소&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="b8b0e-129">Session Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
