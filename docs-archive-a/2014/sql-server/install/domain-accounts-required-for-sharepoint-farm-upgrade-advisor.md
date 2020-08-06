---
title: SharePoint 팜에 필요한 도메인 계정 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d180fbc12a264256156c878916838f7caeec723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660870"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a><span data-ttu-id="5ca70-102">SharePoint 팜에 도메인 계정이 필요함(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="5ca70-102">Domain accounts required for SharePoint farm (Upgrade Advisor)</span></span>
  <span data-ttu-id="5ca70-103">팜 환경용으로 구성되는 SharePoint 제품에서는 도메인 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-103">SharePoint products that are configured for a farm environment require that you use domain accounts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="5ca70-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="5ca70-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="5ca70-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5ca70-105">Component</span></span>  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a><span data-ttu-id="5ca70-106">Description</span><span class="sxs-lookup"><span data-stu-id="5ca70-106">Description</span></span>  
 <span data-ttu-id="5ca70-107">팜 환경용으로 구성되는 SharePoint 제품에서는 서비스 및 데이터베이스 연결에 도메인 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-107">SharePoint products that are configured for a farm environment require that you use domain accounts for services and database connections.</span></span> <span data-ttu-id="5ca70-108">여기에는 Reporting Services 서비스 계정으로 지정한 계정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-108">This includes the account you have specified for the Reporting Services service account.</span></span>  
  
 <span data-ttu-id="5ca70-109">Reporting Services에 대해 도메인 사용자 계정을 사용하지 않는 경우 문제가 표시되는 위치는 SharePoint 2010 중앙 관리 페이지뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-109">SharePoint 2010 Central Administration pages are one place you will see problems if you are not using a domain user account for Reporting Services.</span></span> <span data-ttu-id="5ca70-110">Reporting Services 통합을 구성하려고 하면 다음과 같은 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-110">When you try to configure Reporting Services integration, you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="5ca70-111">"보고서 서버가 SharePoint 팜 설치에서 지원되지 않는 기본 제공 NT AUTHORITY\NETWORK SERVICE 계정으로 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-111">"The report server is running under the built-in NT AUTHORITY\NETWORK SERVICE account, which is not supported by a SharePoint farm installation.</span></span> <span data-ttu-id="5ca70-112">도메인 계정으로 실행되도록 보고서 서버를 다시 구성하십시오."</span><span class="sxs-lookup"><span data-stu-id="5ca70-112">Please reconfigure the report server to run under a domain account."</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5ca70-113">수정 동작</span><span class="sxs-lookup"><span data-stu-id="5ca70-113">Corrective Action</span></span>  
 <span data-ttu-id="5ca70-114">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 및 이전 버전의 경우 Reporting Services 구성 관리자를 사용 하 여 보고서 서버 서비스 계정으로 할당 된 계정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-114">For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and previous versions, use the Reporting Services Configuration Manager to change the account that is assigned as the report server service account.</span></span>  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a><span data-ttu-id="5ca70-115">구성 관리자에서 서비스 계정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="5ca70-115">To change the service account from Configuration Manager</span></span>  
  
1.  <span data-ttu-id="5ca70-116">**시작** 메뉴에서 **모든 프로그램**을 선택 하 고 **Microsoft SQL Server 2008 R2**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-116">From the **Start** menu, select **All Programs**, and then click **Microsoft SQL Server 2008 R2**.</span></span>  
  
2.  <span data-ttu-id="5ca70-117">**구성 도구**를 선택 하 고 **Reporting Services 구성 관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-117">Select **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="5ca70-118">Configuration Manager에서 **서비스 계정** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-118">In Configuration Manager, select the **Service Account** tab.</span></span>  
  
4.  <span data-ttu-id="5ca70-119">**다른 계정 사용** 을 선택 하 고 도메인 계정에 대 한 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-119">Select **Use another account** and enter the credentials for a domain account.</span></span>  
  
5.  <span data-ttu-id="5ca70-120">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ca70-120">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca70-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ca70-121">See Also</span></span>  
 [<span data-ttu-id="5ca70-122">보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="5ca70-122">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
