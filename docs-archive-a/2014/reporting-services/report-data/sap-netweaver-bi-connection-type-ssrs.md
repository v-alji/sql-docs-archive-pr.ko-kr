---
title: SAP NetWeaver BI 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42806e370e20257f5de9e49d4f59dd3bb7793f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742852"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a><span data-ttu-id="e21ca-102">SAP NetWeaver BI 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="e21ca-102">SAP NetWeaver BI Connection Type (SSRS)</span></span>
  <span data-ttu-id="e21ca-103">보고서에 SAP NetWeaver® Business Intelligence 외부 데이터 원본의 데이터를 포함하려면 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]유형의 보고서 데이터 원본에 기초하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-103">To include data from a SAP NetWeaver® Business Intelligence external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span> <span data-ttu-id="e21ca-104">이 기본 제공 데이터 원본 유형은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]의 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-104">This built-in data source type is based on the data extension for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span>  
  
 <span data-ttu-id="e21ca-105">이 데이터 확장 프로그램을 사용하면 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 외부 데이터 원본에 정의된 InfoCube, MultiProvider(가상 InfoCube) 및 웹 사용이 가능한 쿼리에서 다차원 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-105">This data extension enables you to retrieve multidimensional data from InfoCubes, MultiProviders (virtual InfoCubes), and Web-enabled queries that are defined on a [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] external data source.</span></span>  
  
 <span data-ttu-id="e21ca-106">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-106">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="e21ca-107">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-107">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="supported-versions"></a><a name="support"></a><span data-ttu-id="e21ca-108">지원 되는 버전</span><span class="sxs-lookup"><span data-stu-id="e21ca-108">Supported Versions</span></span>  
 <span data-ttu-id="e21ca-109">이 데이터 공급자는 SAP BW 3.5 및 7.0에 대해 개발되고 테스트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-109">The data provider has been developed for and tested against SAP BW 3.5 and 7.0.</span></span>  
  
-   <span data-ttu-id="e21ca-110">SAP BW 3.5 및 7.0에 대한 지원 패키지 20</span><span class="sxs-lookup"><span data-stu-id="e21ca-110">Support Package 20 for SAP BW 3.5 and 7.0</span></span>  
  
 <span data-ttu-id="e21ca-111">Windows 통합 인증을 위해 이 공급자는 다음 시스템에 대해 개발되고 테스트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-111">For Windows Integrated Authentication the provider was developed for and tested against the following systems.</span></span>  
  
-   <span data-ttu-id="e21ca-112">SAP 포털 6.40의 지원 패키지 20</span><span class="sxs-lookup"><span data-stu-id="e21ca-112">SAP Portals 6.40 Support Package 20</span></span>  
  
-   <span data-ttu-id="e21ca-113">SAP Portal 7.0 지원 패키지 11</span><span class="sxs-lookup"><span data-stu-id="e21ca-113">SAP Portals 7.0 Support Package 11</span></span>  
  
-   <span data-ttu-id="e21ca-114">SAP Duet 1.0</span><span class="sxs-lookup"><span data-stu-id="e21ca-114">SAP Duet 1.0</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="e21ca-115">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="e21ca-115">Connection String</span></span>  
 <span data-ttu-id="e21ca-116">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-116">Contact the database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="e21ca-117">다음 연결 문자열 예에서는 SOAP를 사용하는 인터넷을 통해 포트 8000과 XMLA(XML for Analysis Services)를 사용하는 서버의 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-117">The following connection string example specifies an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source on a server using port 8000 and XML for Analysis Services (XMLA) over the Internet using SOAP:</span></span>  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 <span data-ttu-id="e21ca-118">연결 문자열 예제는 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-118">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="e21ca-119">자격 증명</span><span class="sxs-lookup"><span data-stu-id="e21ca-119">Credentials</span></span>  
 <span data-ttu-id="e21ca-120">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-120">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="e21ca-121">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-121">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="e21ca-122">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-122">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="e21ca-123">쿼리</span><span class="sxs-lookup"><span data-stu-id="e21ca-123">Queries</span></span>  
 <span data-ttu-id="e21ca-124">디자인 모드나 쿼리 모드의 그래픽 쿼리 디자이너에서 데이터 원본의 기본 데이터 구조를 찾아서 MDX(Multidimensional Expression) 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-124">You can use the graphical query designer in Design or Query mode to build a Multidimensional Expression (MDX) query by browsing the underlying data structures on the data source.</span></span> <span data-ttu-id="e21ca-125">또한 디자인 타임에 쿼리 디자이너에서 대화형으로 쿼리를 실행하여 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-125">At design time, you can interactively run a query from the query designer to see the results.</span></span> <span data-ttu-id="e21ca-126">작성한 쿼리는 데이터 세트의 필드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-126">The query you build defines fields in the dataset.</span></span> <span data-ttu-id="e21ca-127">실제 데이터는 런타임에 데이터 원본에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-127">At run time, the actual data is returned from the data source.</span></span> <span data-ttu-id="e21ca-128">그래픽 쿼리 디자이너를 사용하여 수행할 수 있는 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-128">Use the graphical query designer to perform the following actions:</span></span>  
  
-   <span data-ttu-id="e21ca-129">디자인 모드에서 데이터 원본의 차원, 멤버, 멤버 속성 및 주요 숫자 값을 데이터 창으로 끌어 MDX(Multidimensional Expression) 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-129">In Design mode, drag dimensions, members, member properties, and key figures from the data source onto a Data pane to build a Multidimensional Expression (MDX) query.</span></span> <span data-ttu-id="e21ca-130">추가 데이터 세트 필드를 정의하려면 계산 멤버 창의 계산 멤버를 데이터 창으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-130">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
-   <span data-ttu-id="e21ca-131">쿼리 모드에서 차원, 멤버, 멤버 속성 및 주요 숫자 값을 쿼리 창으로 끌거나 MDX 텍스트를 쿼리 창에 직접 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-131">In Query mode, drag dimensions, members, member properties, and key figures onto the Query pane or type MDX text directly into the Query pane.</span></span> <span data-ttu-id="e21ca-132">추가 데이터 세트 필드를 정의하려면 계산 멤버 창의 계산 멤버를 데이터 창으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-132">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
 <span data-ttu-id="e21ca-133">쿼리를 작성하면 쿼리 디자이너가 기본 속성을 MDX 쿼리에 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-133">As you build queries, the query designer automatically adds default properties to the MDX query.</span></span> <span data-ttu-id="e21ca-134">기본 속성 이외의 속성을 포함하려면 MDX 쿼리를 직접 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-134">To include properties other than default properties, you must manually modify the MDX query.</span></span>  
  
 <span data-ttu-id="e21ca-135">이 쿼리 디자이너 사용에 대한 자세한 내용은 [SAP NetWeaver BI 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-135">For more information about working with this query designer, see [SAP NetWeaver BI Query Designer User Interface &#40;Report Builder&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md).</span></span>  
  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> <span data-ttu-id="e21ca-136">확장 필드 속성</span><span class="sxs-lookup"><span data-stu-id="e21ca-136">Extended Field Properties</span></span>  
 <span data-ttu-id="e21ca-137">[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 데이터 원본은 확장 필드 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-137">The [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source supports extended field properties.</span></span> <span data-ttu-id="e21ca-138">확장 필드 속성은 `Value` 및 `IsMissing` 외에 데이터 처리 확장 프로그램에서 데이터 세트 필드에 대해 정의한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-138">Extended field properties are properties in addition to `Value` and `IsMissing` that are defined for a dataset field by the data processing extension.</span></span> <span data-ttu-id="e21ca-139">확장 속성에는 미리 정의된 속성과 사용자 지정 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-139">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="e21ca-140">미리 정의된 속성은 여러 데이터 원본에 공통된 속성이고</span><span class="sxs-lookup"><span data-stu-id="e21ca-140">Predefined properties are properties common to multiple data sources.</span></span> <span data-ttu-id="e21ca-141">사용자 지정 속성은 각 데이터 원본에 고유한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-141">Custom properties are unique to each data source.</span></span>  
  
### <a name="working-with-field-properties"></a><span data-ttu-id="e21ca-142">필드 속성 사용</span><span class="sxs-lookup"><span data-stu-id="e21ca-142">Working with Field Properties</span></span>  
 <span data-ttu-id="e21ca-143">확장 필드 속성은 보고서 데이터 창에 보고서 레이아웃으로 끌 수 있는 항목으로 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-143">Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout.</span></span> <span data-ttu-id="e21ca-144">대신 속성의 부모 필드를 보고서로 끈 다음 기본 속성 `Value`를 사용하려는 속성으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-144">Instead, you drag the parent field of the property onto the report and then change the default property from `Value` to the property you want to use.</span></span> <span data-ttu-id="e21ca-145">예를 들어 MDX 쿼리 디자이너에서 메타데이터 창의 수준을 쿼리 창으로 끌어 **Calendar Year/Month Level 01** 이라는 필드를 만든 경우에는 식에서 다음 구문을 사용하여 사용자 지정 확장 속성 **Long Name** 을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-145">For example, if the field name **Calendar Year/Month Level 01** is created in an MDX query designer by dropping a level from the Metadata pane onto the Query pane, you would refer to the custom extended property **Long Name** in an expression using the following syntax:</span></span>  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 <span data-ttu-id="e21ca-146">메타데이터 창에서 필드를 가리키면 확장 필드 속성 이름이 도구 설명에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-146">The name for an extended field property appears in the ToolTip when you hover over a field in the Metadata pane.</span></span> <span data-ttu-id="e21ca-147">기본 데이터를 탐색할 때 사용할 수 있는 쿼리 디자이너에 대한 자세한 내용은 [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-147">For more information about the query designers you can use to explore the underlying data, see [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e21ca-148">보고서가 실행되어 해당 데이터 세트에 대한 데이터를 검색할 때 데이터 원본에서 확장 필드 속성에 대한 값을 제공하는 경우에만 이러한 속성에 대한 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-148">Values exist for extended field properties only if the data source provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="e21ca-149">그러면 아래 설명하는 구문을 사용하여 식에서 해당 `Field` 속성 값을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-149">You can then refer to those `Field` property values from any expression using the syntax described below.</span></span> <span data-ttu-id="e21ca-150">그러나 이러한 필드는 해당 데이터 공급자와만 관련이 있고 보고서 정의 언어에는 포함되지 않으므로 이러한 값을 변경해도 보고서 정의에는 변경된 값이 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-150">However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.</span></span>  
  
 <span data-ttu-id="e21ca-151">식에서 미리 정의된 확장 속성을 참조하려면 다음 구문 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-151">Use either of the following syntaxes to refer to predefined extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="e21ca-152">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="e21ca-152">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="e21ca-153">*필드인! FieldName ("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="e21ca-153">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="e21ca-154">식에서 사용자 지정 확장 속성을 참조하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-154">Use the following syntax to refer to custom extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="e21ca-155">*필드인! FieldName ("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="e21ca-155">*Fields!FieldName("PropertyName")*</span></span>  
  
  
  
### <a name="predefined-field-properties"></a><span data-ttu-id="e21ca-156">미리 정의된 필드 속성</span><span class="sxs-lookup"><span data-stu-id="e21ca-156">Predefined Field Properties</span></span>  
 <span data-ttu-id="e21ca-157">다음 표에서는 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 데이터 원본에 사용할 수 있는 미리 정의된 필드 속성 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-157">The following table provides a list of predefined field properties that you can use for an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source.</span></span>  
  
|<span data-ttu-id="e21ca-158">**Property**</span><span class="sxs-lookup"><span data-stu-id="e21ca-158">**Property**</span></span>|<span data-ttu-id="e21ca-159">**Type**</span><span class="sxs-lookup"><span data-stu-id="e21ca-159">**Type**</span></span>|<span data-ttu-id="e21ca-160">**설명 또는 필요한 값**</span><span class="sxs-lookup"><span data-stu-id="e21ca-160">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="e21ca-161">필드의 데이터 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-161">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="e21ca-162">필드가 결과 데이터 집합에 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-162">Indicates whether the field was found in the resulting data set.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="e21ca-163">주요 숫자 값의 형식화된 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-163">Returns a formatted value for a key figure.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="e21ca-164">필드에 대해 데이터베이스에 정의된 배경색을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-164">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="e21ca-165">항목에 대해 데이터베이스에 정의된 전경색을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-165">Returns the foreground color defined in the database for the item.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="e21ca-166">수준의 키를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-166">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="e21ca-167">부모-자식 계층에 대해 수준 또는 차원 번호를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-167">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="e21ca-168">부모-자식 계층에 대해 부모 수준의 정규화된 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-168">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="e21ca-169">수준의 정규화된 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-169">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="e21ca-170">예를 들어 `UniqueName` 직원의 값은 *[0D_Company]. [ 10D_Department]. [11]*.</span><span class="sxs-lookup"><span data-stu-id="e21ca-170">For example, the `UniqueName` value for an employee might be *[0D_Company].[10D_Department].[11]*.</span></span>|  
  
 <span data-ttu-id="e21ca-171">식에서 필드 및 필드 속성을 사용하는 방법은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-171">For more information about using fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="e21ca-172">주의</span><span class="sxs-lookup"><span data-stu-id="e21ca-172">Remarks</span></span>  
 <span data-ttu-id="e21ca-173">이 데이터 공급자는 일부 보고서 배달 모드만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-173">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="e21ca-174">이 데이터 처리 확장 프로그램에서는 데이터 기반 구독을 통한 보고서 배달이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-174">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="e21ca-175">자세한 내용은 [구독자 데이터에 외부 데이터 원본 사용&#40;데이터 기반 구독&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-175">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
 <span data-ttu-id="e21ca-176">자세한 내용은 [SAP NetWeaver Business Intelligence와 함께 SQL Server 2008 Reporting Services 사용](https://go.microsoft.com/fwlink/?LinkId=167352)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21ca-176">For more information, see [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="e21ca-177">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="e21ca-177">How-To Topics</span></span>  
 <span data-ttu-id="e21ca-178">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-178">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="e21ca-179">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-179">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="e21ca-180">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-180">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="e21ca-181">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-181">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="e21ca-182">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="e21ca-182">Related Sections</span></span>  
 <span data-ttu-id="e21ca-183">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-183">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="e21ca-184">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-184">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="e21ca-185">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-185">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="e21ca-186">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="e21ca-186">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="e21ca-187">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-187">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="e21ca-188">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-188">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="e21ca-189">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-189">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="e21ca-190">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-190">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="e21ca-191">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-191">Provides information about the dataset field collection generated by the query.</span></span>  
  
 [<span data-ttu-id="e21ca-192">Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="e21ca-192">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 <span data-ttu-id="e21ca-193">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ca-193">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="e21ca-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e21ca-194">See Also</span></span>  
 <span data-ttu-id="e21ca-195">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e21ca-195">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e21ca-196">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e21ca-196">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e21ca-197">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e21ca-197">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
