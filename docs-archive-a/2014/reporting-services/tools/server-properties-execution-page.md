---
title: 서버 속성(실행 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ec8725a0cec9e15cb6d8402f8d654320c38471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652010"
---
# <a name="server-properties-execution-page"></a><span data-ttu-id="394b0-102">서버 속성(실행 페이지)</span><span class="sxs-lookup"><span data-stu-id="394b0-102">Server Properties (Execution Page)</span></span>
  <span data-ttu-id="394b0-103">이 페이지를 사용하여 보고서 실행 제한 시간 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-103">Use this page to set a timeout value for report execution.</span></span> <span data-ttu-id="394b0-104">이 값은 현재 보고서 서버 인스턴스에서 처리하는 모든 보고서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-104">This value applies to all reports that are processed by the current report server instance.</span></span> <span data-ttu-id="394b0-105">개별 보고서에 대해 이 값을 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-105">You can override this value for individual reports.</span></span> <span data-ttu-id="394b0-106">보고서 서버에서 수행되는 모든 보고서 처리와 보고서 서버가 보고서에 사용되는 데이터를 검색할 때 데이터베이스에서 수행되는 쿼리 처리를 감안하여 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-106">The value you specify must accommodate all report processing that occurs on the report server, plus query processing performed on the database server when the report server retrieves data that is used in the report.</span></span>  
  
 <span data-ttu-id="394b0-107">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버 인스턴스에 연결한 다음 보고서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="394b0-108">**실행** 을 클릭하여 이 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-108">Click **Execution** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="394b0-109">옵션</span><span class="sxs-lookup"><span data-stu-id="394b0-109">Options</span></span>  
 <span data-ttu-id="394b0-110">**보고서 실행 시간을 제한 안 함**</span><span class="sxs-lookup"><span data-stu-id="394b0-110">**Do not timeout report execution**</span></span>  
 <span data-ttu-id="394b0-111">보고서 서버에서 보고서 처리를 완료하는 시간을 제한하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-111">Allow a report server unlimited time to complete report processing.</span></span>  
  
 <span data-ttu-id="394b0-112">**보고서 실행 시간을 다음으로 제한(초)**</span><span class="sxs-lookup"><span data-stu-id="394b0-112">**Limit report execution to the following number of seconds**</span></span>  
 <span data-ttu-id="394b0-113">보고서 실행에 대한 시간 제약을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-113">Set a time constraint on report execution.</span></span> <span data-ttu-id="394b0-114">시간은 보고서 요청 시점부터 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-114">The time period starts when the report is requested.</span></span> <span data-ttu-id="394b0-115">보고서가 완전히 처리되기 전에 제한 시간에 도달하면 보고서 서버에서는 해당 프로세스 및 외부 데이터 원본에 대한 in-process 쿼리를 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="394b0-115">If the time period ends before the report is fully processed, the report server cancels the process and any in-process queries to external data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394b0-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="394b0-116">See Also</span></span>  
 <span data-ttu-id="394b0-117">[보고서 서버 속성 설정&#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="394b0-117">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="394b0-118">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="394b0-118">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="394b0-119">[보고서 처리 속성 설정](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="394b0-119">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="394b0-120">[보고서 및 공유 데이터 세트 처리에 대한 제한 시간 값 설정&#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="394b0-120">[Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md) </span></span>  
 [<span data-ttu-id="394b0-121">Management Studio의 보고서 서버 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="394b0-121">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
