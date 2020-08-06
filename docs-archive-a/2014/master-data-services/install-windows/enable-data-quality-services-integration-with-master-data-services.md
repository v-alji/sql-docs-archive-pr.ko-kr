---
title: Master Data Services로 Data Quality Services 통합 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649114"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a><span data-ttu-id="4cec2-102">MDS(Master Data Services)와 Data Quality Services의 통합 설정</span><span class="sxs-lookup"><span data-stu-id="4cec2-102">Enable Data Quality Services Integration with Master Data Services</span></span>
  <span data-ttu-id="4cec2-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서 일치 기능은 DQS(Data Quality Services)에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], matching functionality is provided by Data Quality Services (DQS).</span></span> <span data-ttu-id="4cec2-104">이 기능은 먼저 설정해야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-104">This functionality must be enabled to be used.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4cec2-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="4cec2-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="4cec2-106">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 애플리케이션 및 데이터베이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-106">A [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web application and database must exist.</span></span>  
  
-   <span data-ttu-id="4cec2-107">Data Quality Services 기능과 데이터 품질 클라이언트는 MDS 데이터베이스를 호스팅하는 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-107">The Data Quality Services feature and the Data Quality Client must be installed on the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the MDS database.</span></span> <span data-ttu-id="4cec2-108">자세한 내용은 [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cec2-108">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
### <a name="to-enable-data-quality-services-integration"></a><span data-ttu-id="4cec2-109">Data Quality Services 통합을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="4cec2-109">To enable Data Quality Services integration</span></span>  
  
1.  <span data-ttu-id="4cec2-110">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-110">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="4cec2-111">왼쪽 창에서 **웹 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-111">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="4cec2-112">**웹 구성** 페이지에서 웹 사이트 및 웹 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-112">On the **Web Configuration** page, select the website and web application.</span></span>  
  
4.  <span data-ttu-id="4cec2-113">**DQS 통합 사용** 섹션에서 **Data Quality Services와 통합 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-113">In the **Enable DQS Integration** section, click **Enable integration with Data Quality Services**.</span></span>  
  
5.  <span data-ttu-id="4cec2-114">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cec2-114">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cec2-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cec2-115">See Also</span></span>  
 <span data-ttu-id="4cec2-116">[Excel용 MDS 추가 기능의 데이터 품질 일치](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="4cec2-116">[Data Quality Matching in the MDS Add-in for Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="4cec2-117">[Microsoft Excel용 Master Data Services 추가 기능](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span><span class="sxs-lookup"><span data-stu-id="4cec2-117">[Master Data Services Add-in for Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span></span>  
 [<span data-ttu-id="4cec2-118">MDS(Master Data Services) 설치</span><span class="sxs-lookup"><span data-stu-id="4cec2-118">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
