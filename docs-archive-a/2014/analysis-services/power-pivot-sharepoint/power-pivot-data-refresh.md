---
title: PowerPivot 데이터 새로 고침 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651326"
---
# <a name="powerpivot-data-refresh"></a><span data-ttu-id="0dcbb-102">PowerPivot 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="0dcbb-102">PowerPivot Data Refresh</span></span>
  <span data-ttu-id="0dcbb-103">PowerPivot 데이터가 포함된 통합 문서를 만든 후 통합 문서를 만들기 위해 원래 사용했던 원본의 업데이트된 정보를 가져오기 위해 쿼리나 명령을 다시 실행하여 정기적으로 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-103">After you create a workbook that contains PowerPivot data, you might want to periodically refresh the data by rerunning a query or command to get updated information from the sources you used originally to create the workbook.</span></span> <span data-ttu-id="0dcbb-104">이 프로세스를 `data refresh`라고 하며, [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]에서 요청 시 또는 SharePoint 팜의 애플리케이션 서버에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로세스로 실행되는 예약된 작업으로 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-104">This process is called `data refresh`, and you can refresh data on demand in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], or as a scheduled operation that runs as an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] process on an application server in a SharePoint farm.</span></span> <span data-ttu-id="0dcbb-105">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0dcbb-106">SharePoint 2010에서 PowerPivot 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="0dcbb-106">PowerPivot Data Refresh with SharePoint 2010</span></span>](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [<span data-ttu-id="0dcbb-107">PowerPivot 무인 데이터 새로 고침 계정 &#40;SharePoint용 PowerPivot를 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="0dcbb-107">Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="0dcbb-108">PowerPivot 데이터 새로 고침 &#40;SharePoint용 PowerPivot에 저장 된 자격 증명 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="0dcbb-108">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [<span data-ttu-id="0dcbb-109">데이터 새로 고침 예약 &#40;SharePoint용 PowerPivot&#41;</span><span class="sxs-lookup"><span data-stu-id="0dcbb-109">Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="0dcbb-110">데이터 새로 고침 기록 보기 &#40;SharePoint용 PowerPivot&#41;</span><span class="sxs-lookup"><span data-stu-id="0dcbb-110">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="0dcbb-111">및 SharePoint Server 2013 Excel Services에서는 PowerPivot 데이터 모델의 데이터 새로 고침에 다른 아키텍처를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-111">and SharePoint Server 2013 Excel Services use a different architecture for data refresh of PowerPivot data models.</span></span> <span data-ttu-id="0dcbb-112">SharePoint 2013 지원 아키텍처는 Excel Services를 기본 구성 요소로 사용하여 PowerPivot 데이터 모델을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-112">The SharePoint 2013 supported architecture utilizes Excel Services as the primary component to load PowerPivot data models.</span></span> <span data-ttu-id="0dcbb-113">이전에 사용한 데이터 새로 고침 아키텍처는 PowerPivot 시스템 서비스와 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 데이터 모델을 로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="0dcbb-113">The previous data refresh architecture used relied on a server running PowerPivot System Service and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in SharePoint mode to load data models.</span></span> <span data-ttu-id="0dcbb-114">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="0dcbb-114">For more information, see the following:</span></span>  
> 
>  -   [<span data-ttu-id="0dcbb-115">PowerPivot Data Refresh with SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="0dcbb-115">PowerPivot Data Refresh with SharePoint 2013</span></span>](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [<span data-ttu-id="0dcbb-116">SharePoint 2013&#41;&#40;통합 문서 업그레이드 및 예약 된 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="0dcbb-116">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
