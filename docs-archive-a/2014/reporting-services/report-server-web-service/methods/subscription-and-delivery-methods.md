---
title: 구독 및 배달 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], delivering
- delivery [Reporting Services]
- methods [Reporting Services], subscription and delivery
- subscriptions [Reporting Services], about subscriptions
ms.assetid: a8637501-1817-4ccc-b07d-dd9ed5608805
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6ae92a6abd5c25b9ab1236a2b5b11429d210cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730136"
---
# <a name="subscription-and-delivery-methods"></a><span data-ttu-id="956b2-102">구독 및 배달 메서드</span><span class="sxs-lookup"><span data-stu-id="956b2-102">Subscription and Delivery Methods</span></span>
  <span data-ttu-id="956b2-103">다음 메서드를 사용하여 카탈로그 항목의 구독 및 배달을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-103">You can use these methods to create and manage subscriptions and delivery of catalog items.</span></span>  
  
|<span data-ttu-id="956b2-104">방법</span><span class="sxs-lookup"><span data-stu-id="956b2-104">Method</span></span>|<span data-ttu-id="956b2-105">작업</span><span class="sxs-lookup"><span data-stu-id="956b2-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|<span data-ttu-id="956b2-106">지정된 항목에 대한 데이터 기반 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-106">Creates a data-driven subscription for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="956b2-107">데이터 기반 구독에 대한 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-107">Returns the properties for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A>|<span data-ttu-id="956b2-108">보고서 서버 데이터베이스 또는 SharePoint 라이브러리에 있는 지정된 항목에 대해 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-108">Creates a subscription for the specified item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSubscription%2A>|<span data-ttu-id="956b2-109">보고서 서버 데이터베이스에서 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-109">Deletes a subscription from the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A>|<span data-ttu-id="956b2-110">구독의 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-110">Returns the properties of a subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListMySubscriptions%2A>|<span data-ttu-id="956b2-111">지정된 카탈로그 항목에 대해 보고서 서버 또는 SharePoint 사이트의 현재 사용자가 만든 구독의 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-111">Retrieves a list of subscriptions that have been created by the current user of the report server or SharePoint site for the given catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>|<span data-ttu-id="956b2-112">지정된 항목에 대해 만든 구독의 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-112">Retrieves a list of subscriptions that have been created for a given item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PrepareQuery%2A>|<span data-ttu-id="956b2-113">데이터 기반 구독에 대한 배달 쿼리를 통해 검색된 필드를 포함하는 데이터 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-113">Returns a data set containing the fields retrieved by the delivery query for a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>|<span data-ttu-id="956b2-114">데이터 기반 구독의 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-114">Sets the values of properties of a data-driven subscription.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>|<span data-ttu-id="956b2-115">구독의 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="956b2-115">Sets the values of properties of a subscription.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="956b2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="956b2-116">See Also</span></span>  
 <span data-ttu-id="956b2-117">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="956b2-117">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="956b2-118">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="956b2-118">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="956b2-119">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="956b2-119">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="956b2-120">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="956b2-120">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
