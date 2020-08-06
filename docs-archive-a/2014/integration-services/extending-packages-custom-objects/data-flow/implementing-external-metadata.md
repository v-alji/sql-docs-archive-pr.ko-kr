---
title: 외부 메타데이터 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a6b77229c528bc08057e662a4b3761d1daf732f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729663"
---
# <a name="implementing-external-metadata"></a><span data-ttu-id="485a6-102">외부 메타데이터 구현</span><span class="sxs-lookup"><span data-stu-id="485a6-102">Implementing External Metadata</span></span>
  <span data-ttu-id="485a6-103">구성 요소와 해당 데이터 원본의 연결이 끊어진 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> 인터페이스를 사용하여 외부 데이터 원본의 열을 기준으로 입력 및 출력 열 컬렉션의 열에 대한 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-103">When a component is disconnected from its data source, you can validate the columns in the input and output column collections against the columns at its external data source by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> interface.</span></span> <span data-ttu-id="485a6-104">이 인터페이스를 사용하면 외부 데이터 원본에 있는 열의 스냅샷을 유지 관리하고 이러한 열을 구성 요소의 입력 및 출력 열 컬렉션에 있는 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-104">This interface lets you maintain a snapshot of the columns at the external data source and map these columns to the columns in the input and output column collection of the component.</span></span>  
  
 <span data-ttu-id="485a6-105">외부 메타데이터 열을 구현하면 추가 열 컬렉션에 대한 유지 관리 및 유효성 검사를 수행해야 하므로 구성 요소 개발의 오버헤드와 복잡성이 늘어나지만 유효성 검사를 위한 고비용의 서버 왕복을 피할 수 있으면 이 개발 작업을 성공적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-105">Implementing external metadata columns adds a layer of overhead and complexity to component development, because you must maintain and validate against an additional column collection, but the ability to avoid expensive round trips to the server for validation may make this development work worthwhile.</span></span>  
  
## <a name="populating-external-metadata-columns"></a><span data-ttu-id="485a6-106">외부 메타데이터 열 채우기</span><span class="sxs-lookup"><span data-stu-id="485a6-106">Populating External Metadata Columns</span></span>  
 <span data-ttu-id="485a6-107">외부 메타데이터 열은 일반적으로 해당하는 입력 또는 출력 열이 만들어질 때 컬렉션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-107">External metadata columns are typically added to the collection when the corresponding input or output column is created.</span></span> <span data-ttu-id="485a6-108">새 열은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> 메서드 호출을 통해 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-108">New columns are created by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> method.</span></span> <span data-ttu-id="485a6-109">그런 다음 열의 속성이 외부 데이터 원본과 일치하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-109">The properties of the column are then set to match the external data source.</span></span>  
  
 <span data-ttu-id="485a6-110">외부 메타데이터 열을 해당하는 입력 또는 출력 열에 매핑하려면 해당 입력 또는 출력 열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 속성에 외부 메타데이터 열의 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-110">The external metadata column is mapped to the corresponding input or output column by assigning the ID of the external metadata column to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property of the input or output column.</span></span> <span data-ttu-id="485a6-111">이렇게 하면 컬렉션의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> 메서드를 사용하여 특정 입력 또는 출력 열에 대한 외부 메타데이터 열을 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-111">This lets you locate the external metadata column easily for a specific input or output column by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> method of the collection.</span></span>  
  
 <span data-ttu-id="485a6-112">다음 예에서는 외부 메타데이터 열을 만든 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 속성을 설정하여 이 열을 외부 열에 매핑하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-112">The following example shows how to create an external metadata column and then map the column to an output column by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property.</span></span>  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a><span data-ttu-id="485a6-113">외부 메타데이터 열을 사용하여 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="485a6-113">Validating with External Metadata Columns</span></span>  
 <span data-ttu-id="485a6-114">유효성 검사를 수행할 때는 추가 열 컬렉션을 기준으로 해야 하므로 외부 메타데이터 열 컬렉션을 유지 관리하는 구성 요소에 대한 추가 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-114">Validation requires additional steps for components that maintain an external metadata column collection, because you must validate against an additional collection of columns.</span></span> <span data-ttu-id="485a6-115">유효성 검사는 연결 시 유효성 검사와 연결 해제 시 유효성 검사로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-115">Validation can be divided into connected validation or disconnected validation.</span></span>  
  
### <a name="connected-validation"></a><span data-ttu-id="485a6-116">연결 시 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="485a6-116">Connected Validation</span></span>  
 <span data-ttu-id="485a6-117">구성 요소가 외부 데이터 원본에 연결되어 있는 경우 입력 또는 출력 컬렉션의 열은 외부 데이터 원본을 기준으로 직접 유효성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-117">When a component is connected to an external data source, the columns in the input or output collections are verified directly against the external data source.</span></span> <span data-ttu-id="485a6-118">외부 메타데이터 컬렉션의 열에 대한 유효성 검사도 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-118">Additionally, the columns in the external metadata collection must be validated.</span></span> <span data-ttu-id="485a6-119">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 **고급 편집기**에서는 외부 메타데이터 컬렉션을 수정할 수 있으며 이 때 컬렉션의 변경 내용은 검색할 수 없으므로 이 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-119">This is required because the external metadata collection can be modified by using the **Advanced Editor** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and changes made to the collection are not detectable.</span></span> <span data-ttu-id="485a6-120">따라서 연결된 상태일 때 구성 요소에서는 외부 메타데이터 열 컬렉션의 열이 계속해서 외부 데이터 원본의 열을 반영하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-120">Therefore, when connected, components must make sure that the columns in the external metadata column collection continue to reflect the columns at the external data source.</span></span>  
  
 <span data-ttu-id="485a6-121">컬렉션의 속성을로 설정 하 여 **고급 편집기** 에서 외부 메타 데이터 컬렉션을 숨기도록 선택할 수 있습니다 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="485a6-121">You may choose to hide the external metadata collection in the **Advanced Editor** by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> property of the collection to `false`.</span></span> <span data-ttu-id="485a6-122">그러나 이렇게 하면 사용자가 입력 또는 출력 컬렉션의 열을 외부 메타데이터 열 컬렉션의 열에 매핑하는 데 사용할 수 있는 편집기의 **열 매핑** 탭도 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-122">However this also hides the **Column Mapping** tab of the editor, which lets users map columns from the input or output collection to the columns in the external metadata column collection.</span></span> <span data-ttu-id="485a6-123">이 속성을 `false`로 설정해도 개발자는 컬렉션을 프로그래밍 방식으로 수정할 수 있지만 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서만 사용되는 구성 요소의 외부 메타데이터 열 컬렉션은 어느 정도 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-123">Setting this property to `false` does not prevent developers from programmatically modifying the collection, but it does provide a level of protection for the external metadata column collection of a component that is used exclusively in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="disconnected-validation"></a><span data-ttu-id="485a6-124">연결 해제 시 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="485a6-124">Disconnected Validation</span></span>  
 <span data-ttu-id="485a6-125">구성 요소가 외부 데이터 원본에 연결되어 있지 않은 경우 입력 또는 출력 컬렉션의 열은 외부 원본이 아니라 외부 메타데이터 컬렉션의 열을 기준으로 유효성이 검사되므로 유효성 검사 과정이 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-125">When a component is disconnected from an external data source, validation is simplified because the columns in the input or output collection are verified directly against the columns in the external metadata collection and not against the external source.</span></span> <span data-ttu-id="485a6-126">외부 데이터 원본에 대한 연결이 설정되어 있지 않거나 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성이 `false`인 경우 구성 요소에서는 연결 해제 시 유효성 검사를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-126">A component should perform disconnected validation when the connection to its external data source has not been established, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="485a6-127">다음 코드 예에서는 외부 메타데이터 열 컬렉션을 기준으로 유효성 검사를 수행하는 구성 요소의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="485a6-127">The following code example demonstrates an implementation of a component that performs validation against its external metadata column collection.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  
  
<span data-ttu-id="485a6-128">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="485a6-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="485a6-129">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="485a6-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="485a6-130">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="485a6-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="485a6-131">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="485a6-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485a6-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="485a6-132">See Also</span></span>  
 [<span data-ttu-id="485a6-133">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="485a6-133">Data Flow</span></span>](../../data-flow/data-flow.md)  
  
  
