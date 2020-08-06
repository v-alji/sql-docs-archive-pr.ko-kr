---
title: '방법: 업그레이드 관리자 분석 마법사 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660309"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="87692-102">방법: 업그레이드 관리자 분석 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="87692-102">How to: Run the Upgrade Advisor Analysis Wizard</span></span>
  <span data-ttu-id="87692-103">업그레이드 관리자 분석 마법사는 업그레이드 관리자 시작 페이지에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-103">You start the Upgrade Advisor Analysis Wizard from the Upgrade Advisor start page.</span></span> <span data-ttu-id="87692-104">이 항목에서는 업그레이드 관리자 분석 마법사를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-104">This topic describes how to run the Upgrade Advisor Analysis Wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87692-105">업그레이드 관리자 분석 마법사를 실행할 때 업그레이드 관리자에서는 보고서를 기본 보고서 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-105">When you run the Upgrade Advisor Analysis Wizard, Upgrade Advisor saves the reports in the default report folder.</span></span> <span data-ttu-id="87692-106">그러나 보고서 뷰어에는 가장 최근에 저장된 다섯 개 보고서만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="87692-106">However, the report viewer displays only the five latest saved reports.</span></span> <span data-ttu-id="87692-107">보고서의 기본 위치는 내 문서 \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 업그레이드 advisor\110\reports입니다.</span><span class="sxs-lookup"><span data-stu-id="87692-107">The default location for the reports is My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.</span></span>  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="87692-108">업그레이드 관리자 분석 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="87692-108">To run the Upgrade Advisor Analysis Wizard</span></span>  
  
1.  <span data-ttu-id="87692-109">업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 분석 마법사 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Analysis Wizard**.</span></span>  
  
2.  <span data-ttu-id="87692-110">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소\*\* 페이지에서 **서버 이름** 상자에 검색할 서버 이름을 입력 한 다음 **검색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-110">On the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components** page, enter the name of the server to scan in the **Server name** box, and then click **Detect**.</span></span> <span data-ttu-id="87692-111">서버 이름을 입력할 때는 다음 지침을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="87692-111">Use the following guidelines for the server name:</span></span>  
  
    -   <span data-ttu-id="87692-112">비클러스터형 인스턴스를 검색 하려면 컴퓨터 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-112">To scan nonclustered instances, enter the computer name.</span></span>  
  
    -   <span data-ttu-id="87692-113">클러스터형 인스턴스를 검색하려면 가상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-113">To scan clustered instances, enter the virtual [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name.</span></span>  
  
    -   <span data-ttu-id="87692-114">클러스터의 노드에 설치 된 비클러스터형 구성 요소를 검색 하려면 노드 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-114">To scan nonclustered components that are installed on a node of a cluster, enter the node name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="87692-115">업그레이드 관리자에서는 클라이언트 연결에 표준 포트(1433)를 사용하도록 설정되지 않은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87692-115">Upgrade Advisor does not support connecting to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is not set to use the standard port (1433) for client connections.</span></span> <span data-ttu-id="87692-116">표준 포트(1433)를 사용하지 않는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하려면 IP 주소와 포트를 사용하여 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87692-116">If you want to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that does not use the standard port (1433), create an alias using the IP address and the port.</span></span> <span data-ttu-id="87692-117">클라이언트 프로토콜을 구성 하 고 인스턴스에 대 한 별칭을 만드는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87692-117">For more information about configuring client protocols and creating an alias for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
    >   
    >  <span data-ttu-id="87692-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]업그레이드 관리자를 실행 하는 컴퓨터에가 설치 되어 있지 않은 경우 **시작**을 클릭 한 다음를 실행 `cliconfg` 합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-118">If you do not have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer on which you are running Upgrade Advisor, click **Start**, and then run  `cliconfg`.</span></span> <span data-ttu-id="87692-119">그러면 \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 네트워크 유틸리티\*\* 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="87692-119">This opens the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility** dialog box.</span></span> <span data-ttu-id="87692-120">**별칭** 탭을 사용하여 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87692-120">Use the **Alias** tab to create the alias.</span></span>  
  
3.  <span data-ttu-id="87692-121">검색된 구성 요소 목록을 검토하고 필요에 따라 선택 내용을 수정한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-121">Review the list of components detected, modify the selections as necessary, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="87692-122">**연결 매개 변수** 페이지에서 검색할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택하고 인증 방법을 선택한 다음 필요한 경우 사용자 이름과 암호 정보를 입력하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-122">On the **Connection Parameters** page, select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you want to scan, select the authentication method and, if necessary, enter user name and password information, and then click **Next**.</span></span>  
  
     <span data-ttu-id="87692-123">기본 인스턴스 이름은 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="87692-123">The default instance name is MSSQLSERVER.</span></span>  
  
5.  <span data-ttu-id="87692-124">선택한 구성 요소에 대해 요청된 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-124">For selected components, enter the requested information.</span></span> <span data-ttu-id="87692-125">개별 대화 상자에 대 한 자세한 내용은 [업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87692-125">For more information about individual dialog boxes, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
6.  <span data-ttu-id="87692-126">**업그레이드 관리자 설정 확인** 페이지에서 입력한 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-126">On the **Confirm Upgrade Advisor Setting** page, review the information that you entered.</span></span> <span data-ttu-id="87692-127">업그레이드 보고서를 제출 하려는 경우 \*\*에 보고서 보내기를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] \*\* 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87692-127">You can select **Send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)]** if you want to submit your upgrade report.</span></span> <span data-ttu-id="87692-128">또한 개인 정보 취급 방침을 검토할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87692-128">You can also review the privacy policy.</span></span>  
  
7.  <span data-ttu-id="87692-129">**실행** 을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-129">Click **Run** to analyze the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
8.  <span data-ttu-id="87692-130">분석이 완료되면 **보고서 시작** 을 클릭하여 검색된 업그레이드 문제를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="87692-130">When the analysis is finished, click **Launch Report** to view the detected upgrade issues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87692-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87692-131">See Also</span></span>  
 <span data-ttu-id="87692-132">[방법: 업그레이드 관리자 시작](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="87692-132">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="87692-133">[업그레이드 관리자 &#40;사용자 인터페이스를 실행 하는 중&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="87692-133">[Running Upgrade Advisor &#40;User Interface&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md) </span></span>  
 [<span data-ttu-id="87692-134">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="87692-134">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
