---
title: 선택적 웹 서비스 개체에 대한 값 생략 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730135"
---
# <a name="omitting-values-for-optional-web-service-objects"></a><span data-ttu-id="c67ef-102">선택적 웹 서비스 개체에 대한 값 생략</span><span class="sxs-lookup"><span data-stu-id="c67ef-102">Omitting Values for Optional Web Service Objects</span></span>
  <span data-ttu-id="c67ef-103">보고서 서버 웹 서비스 복합 유형의 속성은 대부분 Specified 속성으로 알려진 동반 속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-103">Properties of several of the Report Server Web service complex types have an accompanying property known as the Specified property.</span></span> <span data-ttu-id="c67ef-104">속성 이름은 원래 속성 이름에 "Specified"라는 단어를 붙여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-104">The name of the property consists of the original property name with the word "Specified" appended to it.</span></span> <span data-ttu-id="c67ef-105">이 속성이 있다면 원래 속성의 값을 가끔씩 생략할 수 있다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-105">The presence of this property indicates that a value for the original property may sometimes be omitted.</span></span> <span data-ttu-id="c67ef-106">이는 WSDL(Web Service Description Language)에서 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 프록시 클래스로 변환하는 데 따른 직접적인 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-106">This is a direct result of the translation from the Web Service Description Language (WSDL) to a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class.</span></span> <span data-ttu-id="c67ef-107">예를 들어, 복합 유형 <xref:ReportService2010.DataSourceDefinition.Enabled%2A>의 웹 서비스 속성 <xref:ReportService2010.DataSourceDefinition>에 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>라는 동반 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-107">For example, the Web service property <xref:ReportService2010.DataSourceDefinition.Enabled%2A> of the complex type <xref:ReportService2010.DataSourceDefinition> has an accompanying property named <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>.</span></span> <span data-ttu-id="c67ef-108">애플리케이션을 구축하는 중 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> 속성의 값을 설정하지 않으려면 <xref:ReportService2010.DataSourceDefinition.Enabled%2A>의 값을 제공할 필요가 없습니다. 그러면 기본값 `true`가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-108">If you are building an application and do not want to set a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you do not have to supply a value for <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; the default value of `true` is used.</span></span> <span data-ttu-id="c67ef-109">그러나 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>를 `false`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-109">However, you still need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> to `false`.</span></span> <span data-ttu-id="c67ef-110"><xref:ReportService2010.DataSourceDefinition.Enabled%2A> 속성에 값을 제공하려면 <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>를 `true`에 해당하는 값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-110">If you supply a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> equal to `true`.</span></span> <span data-ttu-id="c67ef-111">이는 쓰기 가능한 속성의 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-111">This is the case for writable properties.</span></span> <span data-ttu-id="c67ef-112">읽기 전용 속성의 경우에는 별다른 조치를 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-112">For read-only properties, you do not need to take any action.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c67ef-113">위에 언급한 기술로 속성을 지정하는 데 실패하면 예기치 않은 웹 서비스 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-113">Failure to specify a property using the above-mentioned technique can result in unpredictable Web service behavior.</span></span>  
  
 <span data-ttu-id="c67ef-114">일반적으로 지정 된 추가 속성을 처리 해야 하는 데이터 형식은 `Boolean` , `DateTime` 및 `Enumeration` 입니다.</span><span class="sxs-lookup"><span data-stu-id="c67ef-114">The data types that usually require you to handle the additional Specified property are `Boolean`, `DateTime`, and `Enumeration`.</span></span>  
  
 <span data-ttu-id="c67ef-115">예제는 <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> 메서드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c67ef-115">For an example, see <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c67ef-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c67ef-116">See Also</span></span>  
 <span data-ttu-id="c67ef-117">[웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="c67ef-117">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="c67ef-118">기술 참조&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c67ef-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
