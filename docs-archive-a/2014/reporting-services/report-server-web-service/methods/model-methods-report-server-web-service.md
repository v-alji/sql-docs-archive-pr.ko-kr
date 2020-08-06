---
title: 모델 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0b93b43383a4b0e5bf19d7c6be9c415d7c91e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736032"
---
# <a name="model-methods"></a><span data-ttu-id="c937a-102">모델 메서드</span><span class="sxs-lookup"><span data-stu-id="c937a-102">Model Methods</span></span>
  <span data-ttu-id="c937a-103">다음 메서드를 사용하여 모델을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-103">You can use these methods to manage models.</span></span>  
  
|<span data-ttu-id="c937a-104">방법</span><span class="sxs-lookup"><span data-stu-id="c937a-104">Method</span></span>|<span data-ttu-id="c937a-105">작업</span><span class="sxs-lookup"><span data-stu-id="c937a-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|<span data-ttu-id="c937a-106">공유 데이터 원본을 기반으로 기본 모델을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-106">Generates a default model on top of a shared data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|<span data-ttu-id="c937a-107">모델 항목과 연결된 사용자 권한을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-107">Retrieves the user permissions that are associated with the model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|<span data-ttu-id="c937a-108">모델 항목과 연결된 정책을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-108">Retrieves the policies that are associated with a model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|<span data-ttu-id="c937a-109">현재 사용자에 대한 모델의 의미 부분을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-109">Returns the semantic piece of a model for the current user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|<span data-ttu-id="c937a-110">모델 항목과 연결된 정책을 삭제하고 모델 항목이 부모의 정책을 상속하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-110">Deletes the policies that are associated with a model item and causes the model item to inherit the policies from its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|<span data-ttu-id="c937a-111">모델의 엔터티와 연결된 드릴스루 보고서를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-111">Lists drillthrough reports that are associated with an entity in a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|<span data-ttu-id="c937a-112">모델 항목 자식 요소의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-112">Returns an array of model item child elements.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|<span data-ttu-id="c937a-113">지원되는 모델 항목 유형 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-113">Returns a list of supported model item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|<span data-ttu-id="c937a-114">사용자가 사용 가능한 모델 및 큐브를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-114">Lists models and perspectives that are available to the user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|<span data-ttu-id="c937a-115">데이터 원본 스키마의 변경 내용을 기반으로 기존 모델을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-115">Updates an existing model based on changes to the data source schema.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|<span data-ttu-id="c937a-116">지정된 모델에서 모델 항목과 연결된 모든 정책을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-116">Deletes all policies that are associated with model items in the specified model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|<span data-ttu-id="c937a-117">드릴스루 보고서 집합을 모델과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-117">Associates a set of drillthrough reports together with a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|<span data-ttu-id="c937a-118">모델 항목에 대한 보안 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c937a-118">Sets security policies on a model item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c937a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c937a-119">See Also</span></span>  
 <span data-ttu-id="c937a-120">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="c937a-120">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="c937a-121">[보고서 서버 웹 서비스](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="c937a-121">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="c937a-122">[보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="c937a-122">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="c937a-123">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c937a-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
