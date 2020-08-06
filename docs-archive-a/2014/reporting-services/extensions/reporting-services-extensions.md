---
title: Reporting Services 확장 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ac942147c75424dae46d9a8e35dc57fba50755f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651520"
---
# <a name="reporting-services-extensions"></a><span data-ttu-id="f1265-102">Reporting Services 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="f1265-102">Reporting Services Extensions</span></span>
  <span data-ttu-id="f1265-103">확장성을 위해 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 의 모듈식 아키텍처를 디자인했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-103">The modular architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="f1265-104">다양한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소에서 사용되는 확장 프로그램을 쉽게 개발, 설치 및 관리할 수 있도록 관리 코드 API를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-104">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="f1265-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 사용하여 프라이빗 또는 공유 어셈블리를 만들 수 있으며 끊임없이 변하는 업무상의 요구에 맞게 새 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-105">You can create private or shared assemblies using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality to meet your evolving business needs.</span></span>  
  
 <span data-ttu-id="f1265-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 고유한 확장성 아키텍처를 통해 개발자는 제품 및 해당 구성 요소의 특정 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-106">The unique extensibility architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables developers to extend specific features of the product and its components.</span></span> <span data-ttu-id="f1265-107">현재 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 데이터 처리 기능을 확장할 수 있도록 폭넓은 지원이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-107">Currently, broad support exists for extending the data processing capabilities of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f1265-108">데이터 처리 API에는 개발자가 추가 데이터 처리를 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에 구축하는 데 사용할 수 있는 친숙한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 공급자 구문 및 규칙이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-108">The data processing API includes familiar, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider constructs and conventions that enable developers to build additional data processing into [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="f1265-109">이러한 데이터 처리 확장 프로그램은 보고서 서버와 보고서 디자이너 모두에 기능을 추가하여 사용자 지정 데이터가 보고서에 완벽하게 통합되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-109">These data processing extensions add functionality to both the Report Server and Report Designer, enabling seamless integration of custom data into reports.</span></span>  
  
 <span data-ttu-id="f1265-110">지원되는 다른 확장 프로그램은 배달 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-110">Another supported extension is the delivery extension.</span></span> <span data-ttu-id="f1265-111">배달 API는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 아키텍처와 완벽하게 통합되어 보고서 알림을 사용자에게 보낼 때 다양한 배달 메커니즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-111">The delivery API is fully integrated with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] architecture, enabling a wide variety of delivery mechanisms to be used when sending report notifications to users.</span></span> <span data-ttu-id="f1265-112">보고서 서버를 확장하여 사용자에게 사용자 지정 배달을 제공할 수 있으며 보고서 관리자의 구독 관리 페이지를 확장하여 사용자 지정 배달 확장 프로그램을 사용하는 구독이 가능하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-112">You can extend the Report Server to provide custom delivery to users and you can extend the subscription management pages of Report Manager to enable subscriptions that use custom delivery extensions.</span></span>  
  
 <span data-ttu-id="f1265-113">또 다른 보고서 서버 확장 프로그램인 RDCE(Report Definition Customization Extension)에서는 보고서 정의가 처리 엔진에 전달되기 전에 보고서 정의를 동적으로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-113">Another report server extension, Report Definition Customization Extension (RDCE), can dynamically customize a report definition before it is passed to the processing engine.</span></span> <span data-ttu-id="f1265-114">사용자나 언어 등의 요소를 기준으로 보고서를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-114">You might customize reports based on factors such as users or languages.</span></span> <span data-ttu-id="f1265-115">예를 들어, 관리자나 부서원과 같이 다양한 사용자가 보는 뷰를 서로 다르게 구현하거나 프랑스어 또는 아랍어로 렌더링될 때 레이아웃이 서로 다르도록 보고서를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-115">For example, you might want to implement different views for various users such as managers or members of a department, or you might want to customize a report to have a different layout when it is rendered in French or Arabic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1265-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f1265-116">In This Section</span></span>  
 [<span data-ttu-id="f1265-117">확장에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="f1265-117">Security Considerations for Extensions</span></span>](security-considerations-for-extensions.md)  
 <span data-ttu-id="f1265-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 확장 프로그램 개발 및 배포와 관련된 보안 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-118">Describes security issues related to developing and deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 [<span data-ttu-id="f1265-119">데이터 처리 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="f1265-119">Implementing a Data Processing Extension</span></span>](data-processing/implementing-a-data-processing-extension.md)  
 <span data-ttu-id="f1265-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대한 데이터 처리 확장 프로그램을 구현하기 위한 요구 사항 및 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-120">Describes the requirements and steps for implementing a data processing extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="f1265-121">배달 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="f1265-121">Implementing a Delivery Extension</span></span>](delivery-extension/implementing-a-delivery-extension.md)  
 <span data-ttu-id="f1265-122">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대한 배달 확장 프로그램을 구현하기 위한 요구 사항 및 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-122">Describes the requirements and steps for implementing a delivery extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="f1265-123">렌더링 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="f1265-123">Implementing a Rendering Extension</span></span>](rendering-extension/implementing-a-rendering-extension.md)  
 <span data-ttu-id="f1265-124">렌더링 확장 프로그램 개발에 대한 소개가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-124">Contains an introduction to developing rendering extensions.</span></span>  
  
 [<span data-ttu-id="f1265-125">보안 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="f1265-125">Implementing a Security Extension</span></span>](security-extension/implementing-a-security-extension.md)  
 <span data-ttu-id="f1265-126">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보안 확장 프로그램을 구현하기 위한 요구 사항 및 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-126">Describes the requirements and steps for implementing a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] security extension.</span></span>  
  
 [<span data-ttu-id="f1265-127">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f1265-127">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
 <span data-ttu-id="f1265-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 확장성 기능용 확장 API 라이브러리에 대한 프로그래밍 참조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1265-128">Contains the programming reference for the extension API library for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensibility features.</span></span>  
  
  
