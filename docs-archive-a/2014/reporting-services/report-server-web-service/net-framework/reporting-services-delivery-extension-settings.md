---
title: Reporting Services 배달 확장 프로그램 설정 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5363c99cb858ce61f7be3b039e27a69944767b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730127"
---
# <a name="reporting-services-delivery-extension-settings"></a><span data-ttu-id="287da-102">Reporting Services 배달 확장 프로그램 설정</span><span class="sxs-lookup"><span data-stu-id="287da-102">Reporting Services Delivery Extension Settings</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="287da-103">에는 메일 배달 확장 프로그램 및 파일 공유 배달 확장 프로그램이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="287da-103">includes an e-mail delivery extension and a file share delivery extension.</span></span> <span data-ttu-id="287da-104">전자 메일 배달 확장 프로그램은 보고서를 개별 사용자 또는 그룹에 전자 메일로 보낼 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-104">E-mail delivery provides a way to send a report to individual users or groups through e-mail.</span></span> <span data-ttu-id="287da-105">파일 공유 배달 확장 프로그램의 경우 렌더링된 보고서를 네트워크의 공유 위치로 자동으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="287da-105">File share delivery enables you to automatically send rendered reports to a share on your network.</span></span> <span data-ttu-id="287da-106">표준 구독 또는 데이터 기반 구독에서 지원되는 배달 확장 프로그램 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="287da-106">You can use either one of the supported delivery extensions with standard subscriptions or data-driven subscriptions.</span></span> <span data-ttu-id="287da-107"><xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> 및 <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> 메서드를 호출할 때마다 배달 확장 프로그램 유형에 대한 특정 배달 설정을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-107">You pass delivery settings that are specific to the type of delivery extension whenever you call the <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>, and <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> methods.</span></span> <span data-ttu-id="287da-108">배달 설정 목록을 프로그래밍 방식으로 검색하려면 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-108">To retrieve a list of delivery settings programmatically, use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="287da-109">배달 확장 프로그램 설정은 대소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-109">Delivery extension settings are case-sensitive.</span></span>  
  
## <a name="e-mail-delivery-settings"></a><span data-ttu-id="287da-110">전자 메일 배달 설정</span><span class="sxs-lookup"><span data-stu-id="287da-110">E-Mail Delivery Settings</span></span>  
 <span data-ttu-id="287da-111">다음 표는 보고서 서버 전자 메일을 사용하는 구독을 위한 전자 메일 배달 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-111">The following table lists the e-mail delivery settings for subscriptions that use report server e-mail.</span></span>  
  
|<span data-ttu-id="287da-112">설정</span><span class="sxs-lookup"><span data-stu-id="287da-112">Setting</span></span>|<span data-ttu-id="287da-113">값</span><span class="sxs-lookup"><span data-stu-id="287da-113">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="287da-114">**받는 사람**</span><span class="sxs-lookup"><span data-stu-id="287da-114">**TO**</span></span>|<span data-ttu-id="287da-115">전자 메일 메시지의 `To` 줄에 표시되는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-115">The e-mail address that appears on the `To` line of the e-mail message.</span></span> <span data-ttu-id="287da-116">여러 개의 전자 메일 주소는 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="287da-116">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="287da-117">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-117">Required.</span></span>|  
|<span data-ttu-id="287da-118">**사람과**</span><span class="sxs-lookup"><span data-stu-id="287da-118">**CC**</span></span>|<span data-ttu-id="287da-119">전자 메일 메시지의 `Cc` 줄에 표시되는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-119">The e-mail address that appears on the `Cc` line of the e-mail message.</span></span> <span data-ttu-id="287da-120">여러 개의 전자 메일 주소는 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="287da-120">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="287da-121">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-121">Optional.</span></span>|  
|<span data-ttu-id="287da-122">**숨은**</span><span class="sxs-lookup"><span data-stu-id="287da-122">**BCC**</span></span>|<span data-ttu-id="287da-123">전자 메일 메시지의 `Bcc` 줄에 표시되는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-123">The e-mail address that appears on the `Bcc` line of the e-mail message.</span></span> <span data-ttu-id="287da-124">여러 개의 전자 메일 주소는 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="287da-124">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="287da-125">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-125">Optional.</span></span>|  
|<span data-ttu-id="287da-126">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="287da-126">**ReplyTo**</span></span>|<span data-ttu-id="287da-127">전자 메일 메시지의 `Reply-To` 머리글에 표시되는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-127">The e-mail address that appears in the `Reply-To` header of the e-mail message.</span></span> <span data-ttu-id="287da-128">값은 단일 전자 메일 주소여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-128">The value must be a single e-mail address.</span></span> <span data-ttu-id="287da-129">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-129">Optional.</span></span>|  
|`IncludeReport`|<span data-ttu-id="287da-130">전자 메일 배달에 보고서를 포함시킬지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-130">A value that indicates whether to include the report in the e-mail delivery.</span></span> <span data-ttu-id="287da-131">`true` 값은 보고서가 전자 메일 메시지의 본문으로 배달됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="287da-131">A value of `true` indicates that the report is delivered in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="287da-132">**RenderFormat**</span><span class="sxs-lookup"><span data-stu-id="287da-132">**RenderFormat**</span></span>|<span data-ttu-id="287da-133">렌더링된 보고서를 생성하는 데 사용할 렌더링 확장 프로그램의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-133">The name of the rendering extension to use to generate the rendered report.</span></span> <span data-ttu-id="287da-134">이름은 보고서 서버에 설치되었으며 표시되는 렌더링 확장 프로그램의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-134">The name must correspond to one of the visible rendering extensions installed on the report server.</span></span> <span data-ttu-id="287da-135">이 값은 `IncludeReport` 설정이 `true` 값으로 설정된 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-135">This value is required if the `IncludeReport` setting is set to a value of `true`.</span></span>|  
|<span data-ttu-id="287da-136">**우선 순위**</span><span class="sxs-lookup"><span data-stu-id="287da-136">**Priority**</span></span>|<span data-ttu-id="287da-137">전자 메일 메시지를 전송하는 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-137">The priority with which the e-mail message is sent.</span></span> <span data-ttu-id="287da-138">유효한 값은 `LOW`, `NORMAL` 및 `HIGH`입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-138">Valid values are `LOW`, `NORMAL`, and `HIGH`.</span></span> <span data-ttu-id="287da-139">기본값은 `NORMAL`입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-139">The default value is `NORMAL`.</span></span>|  
|<span data-ttu-id="287da-140">**Subject**</span><span class="sxs-lookup"><span data-stu-id="287da-140">**Subject**</span></span>|<span data-ttu-id="287da-141">전자 메일 메시지의 제목 줄 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-141">The text in the subject line of the e-mail message.</span></span>|  
|<span data-ttu-id="287da-142">**설명**</span><span class="sxs-lookup"><span data-stu-id="287da-142">**Comment**</span></span>|<span data-ttu-id="287da-143">전자 메일 메시지의 본문에 포함된 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-143">The text included in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="287da-144">**IncludeLink**</span><span class="sxs-lookup"><span data-stu-id="287da-144">**IncludeLink**</span></span>|<span data-ttu-id="287da-145">전자 메일 본문에 보고서에 대한 링크를 포함시킬지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-145">A value that indicates whether to include a link to the report in the body of the e-mail.</span></span>|  
  
## <a name="file-share-delivery-settings"></a><span data-ttu-id="287da-146">파일 공유 배달 설정</span><span class="sxs-lookup"><span data-stu-id="287da-146">File Share Delivery Settings</span></span>  
 <span data-ttu-id="287da-147">다음 표는 구독을 위한 파일 공유 배달 설정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="287da-147">The following table lists the file share delivery settings for subscriptions.</span></span>  
  
|<span data-ttu-id="287da-148">설정</span><span class="sxs-lookup"><span data-stu-id="287da-148">Setting</span></span>|<span data-ttu-id="287da-149">값</span><span class="sxs-lookup"><span data-stu-id="287da-149">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="287da-150">**이름도**</span><span class="sxs-lookup"><span data-stu-id="287da-150">**FILENAME**</span></span>|<span data-ttu-id="287da-151">디스크에 저장되는 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-151">The name of the file that is saved to disk.</span></span>|  
|<span data-ttu-id="287da-152">**FILEEXTN**</span><span class="sxs-lookup"><span data-stu-id="287da-152">**FILEEXTN**</span></span>|<span data-ttu-id="287da-153">렌더링된 보고서에 대한 파일 확장명을 포함시킬지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="287da-153">Indicates whether to include a file extension for the rendered report.</span></span> <span data-ttu-id="287da-154">값은 `true` 또는 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-154">The value is either `true` or `false`.</span></span>|  
|<span data-ttu-id="287da-155">**PATH**</span><span class="sxs-lookup"><span data-stu-id="287da-155">**PATH**</span></span>|<span data-ttu-id="287da-156">보고서를 저장할 폴더 경로 또는 UNC 파일 공유 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-156">The folder path or UNC file share path to which to save the report.</span></span>|  
|<span data-ttu-id="287da-157">**RENDER_FORMAT**</span><span class="sxs-lookup"><span data-stu-id="287da-157">**RENDER_FORMAT**</span></span>|<span data-ttu-id="287da-158">디스크에 저장되는 보고서의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-158">The format of the report that is saved to disk.</span></span>|  
|<span data-ttu-id="287da-159">**이름**</span><span class="sxs-lookup"><span data-stu-id="287da-159">**USERNAME**</span></span>|<span data-ttu-id="287da-160">네트워크 리소스 또는 디스크에 액세스하는 데 필요한 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-160">The username required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="287da-161">**암호**</span><span class="sxs-lookup"><span data-stu-id="287da-161">**PASSWORD**</span></span>|<span data-ttu-id="287da-162">네트워크 리소스 또는 디스크에 액세스하는 데 필요한 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-162">The password required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="287da-163">**WRITEMODE**</span><span class="sxs-lookup"><span data-stu-id="287da-163">**WRITEMODE**</span></span>|<span data-ttu-id="287da-164">디스크에 액세스할 때 사용할 쓰기 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-164">The write mode to use when accessing the disk.</span></span> <span data-ttu-id="287da-165">유효한 값은 `None`, `Overwrite` 및 `AutoIncrement`입니다.</span><span class="sxs-lookup"><span data-stu-id="287da-165">Valid values are `None`, `Overwrite`, and `AutoIncrement`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="287da-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="287da-166">See Also</span></span>  
 <span data-ttu-id="287da-167">[SSRS&#41;&#40;기술 참조](../../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="287da-167">[Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="287da-168">웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="287da-168">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
