---
title: ISSCommandWithParameters(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
ms.openlocfilehash: 295026497a97b4ce13d1a1a68de48079809390ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649035"
---
# <a name="isscommandwithparameters-ole-db"></a><span data-ttu-id="14a73-102">ISSCommandWithParameters(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="14a73-102">ISSCommandWithParameters (OLE DB)</span></span>
  <span data-ttu-id="14a73-103">**ISSCommandWithParameters** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 및 UDT(사용자 정의 형식)에 대한 지원을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-103">**ISSCommandWithParameters** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT).</span></span> <span data-ttu-id="14a73-104">이 인터페이스는 선택적 인터페이스이며 핵심 OLE DB 인터페이스인 **ICommandWithParameters**에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-104">This is an optional interface that inherits from the core OLE DB interface **ICommandWithParameters**.</span></span> <span data-ttu-id="14a73-105">**ICommandWithParameters**에서 상속되는 3개의 메서드인 **GetParameterInfo**, **MapParameterNames**및 **SetParameterInfo**외에도 **ISSCommandWithParameters** 는 서버별 데이터 형식을 처리하는 데 사용되는 두 개의 새 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-105">In addition to the three methods inherited from **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, and **SetParameterInfo**; **ISSCommandWithParameters** provides two new methods that are used to handle server specific data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14a73-106"> 서비스 구성 요소가 사용되는 경우 **ISSCommandWithParameters** 인터페이스를 사용할 수 있지만 서비스 구성 요소 자체는 이 인터페이스를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-106">The **ISSCommandWithParameters** interface can be used when Service Components are used, but the Service Components themselves will not use this interface.</span></span>  
  
|<span data-ttu-id="14a73-107">방법</span><span class="sxs-lookup"><span data-stu-id="14a73-107">Method</span></span>|<span data-ttu-id="14a73-108">Description</span><span class="sxs-lookup"><span data-stu-id="14a73-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14a73-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="14a73-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-getparameterproperties-ole-db.md)|<span data-ttu-id="14a73-110">명령에 전달된 각 UDT 또는 XML 매개 변수에 대해 배열의 **SSPARAMPROPS** 속성 집합 구조를 하나씩 반환하지만 다른 유형의 매개 변수에 대해서는 아무 것도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-110">Returns one **SSPARAMPROPS** property set structure in the array for each UDT or XML parameter passed to the command, but none is returned for other types of parameters.</span></span>|  
|[<span data-ttu-id="14a73-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="14a73-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-setparameterproperties-ole-db.md)|<span data-ttu-id="14a73-112">매개 변수별 서수로 매개 변수 속성을 설정하거나, **SSPARAMPROPS** 구조의 배열을 지정하여 대량 매개 변수 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14a73-112">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of **SSPARAMPROPS** structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14a73-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14a73-113">See Also</span></span>  
 <span data-ttu-id="14a73-114">[인터페이스 &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="14a73-114">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="14a73-115">[XML 데이터 형식 사용](../native-client/features/using-xml-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="14a73-115">[Using XML Data Types](../native-client/features/using-xml-data-types.md) </span></span>  
 [<span data-ttu-id="14a73-116">사용자 정의 형식 사용</span><span class="sxs-lookup"><span data-stu-id="14a73-116">Using User-Defined Types</span></span>](../native-client/features/using-user-defined-types.md)  
  
  
