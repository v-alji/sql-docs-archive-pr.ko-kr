---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: rothja
ms.author: jroth
ms.openlocfilehash: df3103181b3cad772e7d1c73068b8864bf591b73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659959"
---
# <a name="icommandwithparameters"></a><span data-ttu-id="7830e-102">ICommandWithParameters</span><span class="sxs-lookup"><span data-stu-id="7830e-102">ICommandWithParameters</span></span>
  <span data-ttu-id="7830e-103">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 데이터베이스 엔진의 기능이 향상되어 ICommandWithParameters::GetParameterInfo를 통해 예상 결과에 대한 보다 정확한 설명을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7830e-103">Improvements in the database engine beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ICommandWithParameters::GetParameterInfo to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="7830e-104">보다 정확한 결과는 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 CommandWithParameters::GetParameterInfo가 반환한 값과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7830e-104">These more accurate results may differ from the values returned by CommandWithParameters::GetParameterInfo in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7830e-105">자세한 내용은 [메타데이터 검색](../native-client/features/metadata-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7830e-105">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="7830e-106">또한 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터는 ICommandWithParameters::SetParameterInfo를 호출할 때 *pwszName* 매개 변수에 전달된 값이 유효한 식별자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7830e-106">Also beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], when calling ICommandWithParameters::SetParameterInfo, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="7830e-107">자세한 내용은 [Database Identifiers](../databases/database-identifiers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7830e-107">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7830e-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7830e-108">See Also</span></span>  
 [<span data-ttu-id="7830e-109">인터페이스&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="7830e-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
