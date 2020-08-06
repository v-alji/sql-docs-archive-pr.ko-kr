---
title: WQL을 사용 하 여 구성 관리용 WMI 공급자 액세스 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b58297c5e292ceb18a6e2e50e2b25b9aa352e2fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638575"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a><span data-ttu-id="087ac-102">WQL을 사용하여 구성 관리용 WMI 공급자 액세스</span><span class="sxs-lookup"><span data-stu-id="087ac-102">Access WMI Provider for Configuration Management using WQL</span></span>
  <span data-ttu-id="087ac-103">이 섹션에서는 컴퓨터 관리용 WMI 공급자에 대해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL(Windows Management Instrumentation Query Language) 문을 실행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-103">This section describes how to execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) statements against the WMI Provider for Computer Management.</span></span>  
  
 <span data-ttu-id="087ac-104">이 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, 네트워크 프로토콜 및 별칭을 열거하기 위해 WQL 편집기인 WBEMtest.exe를 사용하여 WMI 공급자에 대해 WQL 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-104">The example uses a WQL editor, WBEMtest.exe, to run WQL queries against the WMI Provider to enumerate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network protocols, and aliases.</span></span>  
  
### <a name="querying-services-using-wbemtest"></a><span data-ttu-id="087ac-105">WBEMtest를 사용하여 서비스 쿼리</span><span class="sxs-lookup"><span data-stu-id="087ac-105">Querying services using WBEMtest</span></span>  
  
1.  <span data-ttu-id="087ac-106">**시작** 메뉴에서 **실행**을 클릭 한 다음를 입력 `WBEMtest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-106">From the **Start** menu, click **Run**, and then enter `WBEMtest`.</span></span>  
  
2.  <span data-ttu-id="087ac-107">WBEMtest.exe 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-107">The WBEMtest.exe dialog appears.</span></span> <span data-ttu-id="087ac-108">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-108">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="087ac-109">첫 번째 텍스트 필드에 컴퓨터 관리용 WMI 공급자 네임스페이스인 root\Microsoft\SqlServer\ComputerManagement11을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-109">In the first text field, type the WMI Provider for Computer Management namespace: root\Microsoft\SqlServer\ComputerManagement11.</span></span> <span data-ttu-id="087ac-110">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-110">Click **Connect**.</span></span>  
  
4.  <span data-ttu-id="087ac-111">**쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-111">Click **Query**.</span></span> <span data-ttu-id="087ac-112">로컬 컴퓨터에서 실행 중인 현재 서비스를 반환 하는 쿼리를 입력 \*\* \* 합니다. Sqlservice에서 선택 합니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="087ac-112">Type a query that returns the current services running on the local computer: **SELECT \* FROM SqlService.**</span></span> <span data-ttu-id="087ac-113">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-113">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="087ac-114">`WHERE ServiceName = "MSSQLSERVER"`를 추가하여 쿼리를 구체화합니다.</span><span class="sxs-lookup"><span data-stu-id="087ac-114">Further refine the query by adding `WHERE ServiceName = "MSSQLSERVER"`.</span></span>  
  
  
