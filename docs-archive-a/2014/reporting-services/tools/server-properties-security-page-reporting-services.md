---
title: 서버 속성(보안 페이지) - Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f709d42bf593b4933d9fc1fdc423c195967df382
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652008"
---
# <a name="server-properties-security-page---reporting-services"></a><span data-ttu-id="31239-102">서버 속성(보안 페이지) - Reporting Services</span><span class="sxs-lookup"><span data-stu-id="31239-102">Server Properties (Security Page) - Reporting Services</span></span>
  <span data-ttu-id="31239-103">이 페이지를 사용하여 보고서 서버를 손상시킬 가능성이 있는 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31239-103">Use this page to turn off features that can potentially compromise a report server.</span></span> <span data-ttu-id="31239-104">이러한 기능을 해제하면 일부 기능이 제한되지만 특정 위협을 완화하여 보고서 서버의 전체적인 보안을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31239-104">Turning off these features will limit some functionality, but can improve the overall security of the report server by mitigating specific threats.</span></span>  
  
 <span data-ttu-id="31239-105">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버 인스턴스에 연결한 다음 보고서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="31239-105">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="31239-106">**보안** 을 클릭하여 이 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="31239-106">Click **Security** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="31239-107">옵션</span><span class="sxs-lookup"><span data-stu-id="31239-107">Options</span></span>  
 <span data-ttu-id="31239-108">**보고서 데이터 원본에 대한 Windows 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="31239-108">**Enable Windows integrated security for report data sources**</span></span>  
 <span data-ttu-id="31239-109">보고서를 요청한 사용자의 Windows 보안 토큰을 사용하여 보고서 데이터 원본에 연결할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31239-109">Specify whether a connection to a report data source can be made using the Windows security token of the user who requested the report.</span></span>  
  
 <span data-ttu-id="31239-110">이 기능을 해제하면 보고서 데이터 원본 속성 페이지의 Windows 통합 보안 기능을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31239-110">If you turn off this feature, the Windows Integrated Security feature in the report data source property pages will be unavailable.</span></span> <span data-ttu-id="31239-111">보고서 데이터 원본이 Windows 통합 보안으로 구성된 상태에서 이 기능을 해제하면 보고서 서버는 모든 데이터 원본 연결 속성을 즉시 업데이트하여 자격 증명을 확인하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="31239-111">If report data sources are configured for Windows integrated security and you subsequently turn off this feature, the report server will immediately update all data source connection properties to prompt for credentials.</span></span>  
  
 <span data-ttu-id="31239-112">**임시 보고 사용**</span><span class="sxs-lookup"><span data-stu-id="31239-112">**Enable Ad Hoc Reporting**</span></span>  
 <span data-ttu-id="31239-113">사용자가 관심 있는 데이터를 클릭할 때 자동으로 새 보고서가 생성되는 보고서 작성기 보고서에서 사용자가 임시 쿼리를 수행할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31239-113">Specify whether users can perform ad hoc queries from a Report Builder report, where new reports are automatically generated when a user clicks data of interest.</span></span>  
  
 <span data-ttu-id="31239-114">이 옵션 설정에 따라 보고서 서버의 `EnableLoadReportDefinition` 속성이 `True` 또는 `False`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="31239-114">Setting this option determines whether the `EnableLoadReportDefinition` property on the report server is set to `True` or `False`.</span></span> <span data-ttu-id="31239-115">이 옵션의 선택을 취소하면 속성은 `False`로 설정되며 보고서 서버는 데이터 탐색 중 작성된 클릭 광고 보고서를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31239-115">If you clear this option, the property will be set to `False` and report server will not generate clickthrough reports that are created during data exploration.</span></span> <span data-ttu-id="31239-116">`LoadReportDefinition` 메서드에 대한 모든 호출은 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="31239-116">All calls to the `LoadReportDefinition` method will be blocked.</span></span>  
  
 <span data-ttu-id="31239-117">이 옵션을 끄면 악의적인 사용자가 `LoadReportDefinition` 요청으로 보고서 서버에 오버로드를 가하여 서비스 거부 공격을 실행할 수 있는 위협이 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="31239-117">Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with `LoadReportDefinition` requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31239-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31239-118">See Also</span></span>  
 <span data-ttu-id="31239-119">[보고서 서버 속성 &#40;Management Studio&#41;설정](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="31239-119">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="31239-120">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="31239-120">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="31239-121">[보고서 데이터 원본에 대 한 자격 증명 및 연결 정보 지정] (.. [Management Studio F1 도움말의/Report-data/specify-credential-and-connection-information-for-report-data-sources.md Report Server](report-server-in-management-studio-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="31239-121">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md [Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md)</span></span>  
  
  
