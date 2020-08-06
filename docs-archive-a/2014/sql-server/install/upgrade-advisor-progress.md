---
title: 업그레이드 관리자 진행률 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b504b8f1c8392ad2cf55837dc65bbb2f019d6f48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650408"
---
# <a name="upgrade-advisor-progress"></a><span data-ttu-id="c32a5-102">업그레이드 관리자 진행률</span><span class="sxs-lookup"><span data-stu-id="c32a5-102">Upgrade Advisor Progress</span></span>
  <span data-ttu-id="c32a5-103">업그레이드 관리자 분석은 선택된 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소의 분석을 수행하는 전용 분석기를 통해 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-103">Upgrade Advisor analysis starts with a dedicated analyzer that performs an analysis of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that you selected.</span></span> <span data-ttu-id="c32a5-104">구성 요소가 분석 되 면 **진행률 대화 상자에 진행률이 보고** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-104">As components are analyzed, progress is reported in the **Progress** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c32a5-105">옵션</span><span class="sxs-lookup"><span data-stu-id="c32a5-105">Options</span></span>  
 <span data-ttu-id="c32a5-106">**동작**</span><span class="sxs-lookup"><span data-stu-id="c32a5-106">**Action**</span></span>  
 <span data-ttu-id="c32a5-107">분석할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-107">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that is selected for analysis.</span></span>  
  
 <span data-ttu-id="c32a5-108">**상태**</span><span class="sxs-lookup"><span data-stu-id="c32a5-108">**Status**</span></span>  
 <span data-ttu-id="c32a5-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소 진행률 인터페이스에서 반환된 상태 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-109">Displays the status value returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component progress interface.</span></span>  
  
 <span data-ttu-id="c32a5-110">**Message**</span><span class="sxs-lookup"><span data-stu-id="c32a5-110">**Message**</span></span>  
 <span data-ttu-id="c32a5-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개별 분석기에서 반환된 오류, 실패 또는 성공 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-111">Displays error, failure, or success messages returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] individual analyzer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c32a5-112">분석이 너무 오래 걸리면 분석을 중지하고 업그레이드 관리자 분석 마법사를 종료한 다음 마법사를 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-112">If the analysis is taking too long, you can stop the analysis, exit the Upgrade Advisor Analysis Wizard, and then rerun the wizard.</span></span> <span data-ttu-id="c32a5-113">분석 시간을 줄이려면 분석할 구성 요소 수를 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="c32a5-113">To reduce analysis time, select fewer components to scan.</span></span>  
  
 <span data-ttu-id="c32a5-114">분석이 완료되면 보고서가 파일로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-114">When analysis is complete, the report is written to a file.</span></span> <span data-ttu-id="c32a5-115">보고서 **시작** 을 클릭 하 여이 페이지에서 보고서 뷰어를 시작 하 여 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-115">You can view the report by clicking **Launch Report** to launch the report viewer from this page.</span></span> <span data-ttu-id="c32a5-116">나중에 보고서를 보려면 업그레이드 관리자 시작 페이지에서 **업그레이드 관리자 보고서 뷰어** 를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-116">If you want to view the report later, you can open the **Upgrade Advisor Report Viewer** from the Upgrade Advisor start page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c32a5-117">이전 보고서는 서버를 분석할 때마다 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-117">Previous reports are saved every time you analyze a server.</span></span> <span data-ttu-id="c32a5-118">보고서는 파일 이름에 타임스탬프를 사용하여 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-118">The reports are saved using the timestamp for the file name.</span></span> <span data-ttu-id="c32a5-119">보고서 뷰어에는 가장 최근에 저장된 다섯 개의 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c32a5-119">The report viewer displays the latest five saved reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c32a5-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c32a5-120">See Also</span></span>  
 <span data-ttu-id="c32a5-121">[방법: 업그레이드 관리자 시작](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="c32a5-121">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="c32a5-122">[방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="c32a5-122">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="c32a5-123">[SQL Server 구성 요소](../../../2014/sql-server/install/sql-server-components.md) </span><span class="sxs-lookup"><span data-stu-id="c32a5-123">[SQL Server Components](../../../2014/sql-server/install/sql-server-components.md) </span></span>  
 <span data-ttu-id="c32a5-124">[업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c32a5-124">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 [<span data-ttu-id="c32a5-125">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="c32a5-125">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
