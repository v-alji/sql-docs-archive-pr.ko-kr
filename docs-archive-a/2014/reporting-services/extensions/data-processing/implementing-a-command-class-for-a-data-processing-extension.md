---
title: 데이터 처리 확장 프로그램에 대한 Command 클래스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f07b9beb798b1cd33ec2fee6af890a09a516b2f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741596"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a><span data-ttu-id="fea7b-102">데이터 처리 확장 프로그램에 대한 Command 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="fea7b-102">Implementing a Command Class for a Data Processing Extension</span></span>
  <span data-ttu-id="fea7b-103">**Command** 개체는 요청을 작성하고 이를 데이터 원본에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-103">The **Command** object formulates a request and passes it on to the data source.</span></span> <span data-ttu-id="fea7b-104">명령 텍스트는 텍스트 및 XML을 비롯하여 다양한 구문 형식을 취할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-104">The command text can take many different syntactical forms, including text and XML.</span></span> <span data-ttu-id="fea7b-105">결과가 반환될 경우 **Command** 개체는 **DataReader** 개체 형태로 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-105">If results are returned, the **Command** object returns results as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="fea7b-106">**Command** 클래스를 만들려면 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-106">To create a **Command** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>.</span></span> <span data-ttu-id="fea7b-107"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 메서드를 구현하여 결과 집합을 **DataReader** 개체 형태로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-107">Implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method to return a result set as a **DataReader** object.</span></span> <span data-ttu-id="fea7b-108">**Command** 클래스의 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 메서드에는 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 열거를 인수로 사용하는 구현이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-108">The <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method of your **Command** class should include an implementation that takes a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> enumeration as an argument.</span></span> <span data-ttu-id="fea7b-109">데이터 처리 확장 프로그램을 보고서 디자이너에 배포할 경우 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> 메서드에서 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 사례를 처리하는 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-109">If you deploy your data processing extension to Report Designer, provide an implementation that handles a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> case in the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="fea7b-110">스키마 전용 구현은 보고서 디자이너에 필드 목록을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-110">A schema-only implementation is used to supply Report Designer with a fields list.</span></span> <span data-ttu-id="fea7b-111"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 메서드를 통해 반환된 **DataReader** 개체에는 결과 집합에서 필드 또는 열에 대한 유형 및 이름 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-111">The **DataReader** object returned by the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method needs to contain type and name information for the fields, or columns, in your result set.</span></span>  
  
 <span data-ttu-id="fea7b-112">선택적으로 **Command** 클래스는 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-112">Optionally, your **Command** class can implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>.</span></span> <span data-ttu-id="fea7b-113">이 인터페이스를 통해 구현 클래스에서 쿼리를 분석하고 쿼리의 매개 변수 목록을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-113">This interface enables an implementing class to analyze a query and return a list of parameters in the query.</span></span> <span data-ttu-id="fea7b-114"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 인터페이스의 기능은 보고서 디자이너에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-114">The functionality of the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> interface is only used in Report Designer.</span></span> <span data-ttu-id="fea7b-115"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현하면 보고서가 미리 보기 모드에서 실행될 때마다 보고서 디자이너 사용자로 하여금 매개 변수를 결정하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-115">When you implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, you enable users of Report Designer to be prompted for parameters whenever a report is run in preview mode.</span></span> <span data-ttu-id="fea7b-116">또한 **데이터 집합** 대화 상자의 **매개 변수** 탭에서 매개 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-116">In addition, you can view the parameters in the **Parameters** tab of the **Data Set** dialog.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fea7b-117">사용자 지정 데이터 처리 확장 프로그램에서 매개 변수를 지원하지 않는 경우 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fea7b-117">You should not implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> if your custom data processing extension does not support parameters.</span></span>  
  
 <span data-ttu-id="fea7b-118">예제 **Command** 클래스 구현은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fea7b-118">For a sample **Command** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea7b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fea7b-119">See Also</span></span>  
 <span data-ttu-id="fea7b-120">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fea7b-120">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="fea7b-121">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="fea7b-121">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="fea7b-122">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="fea7b-122">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
