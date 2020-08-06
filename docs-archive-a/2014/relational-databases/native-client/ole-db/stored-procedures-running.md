---
title: 저장 프로시저 실행(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e6ce951f343002feea5aa793d0cc2092422b819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738199"
---
# <a name="running-stored-procedures-ole-db"></a><span data-ttu-id="0a8ce-102">저장 프로시저 실행(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="0a8ce-102">Running Stored Procedures (OLE DB)</span></span>
  <span data-ttu-id="0a8ce-103">문을 실행할 때 클라이언트 애플리케이션에서 직접 문을 실행하거나 준비하는 대신 데이터 원본의 저장 프로시저를 호출하면 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-103">When executing statements, calling a stored procedure on the data source (instead of executing or preparing a statement in the client application directly) can provide:</span></span>  
  
-   <span data-ttu-id="0a8ce-104">성능 향상</span><span class="sxs-lookup"><span data-stu-id="0a8ce-104">Higher performance.</span></span>  
  
-   <span data-ttu-id="0a8ce-105">네트워크 오버헤드 감소</span><span class="sxs-lookup"><span data-stu-id="0a8ce-105">Reduced network overhead.</span></span>  
  
-   <span data-ttu-id="0a8ce-106">일관성 향상</span><span class="sxs-lookup"><span data-stu-id="0a8ce-106">Better consistency.</span></span>  
  
-   <span data-ttu-id="0a8ce-107">정확성 향상</span><span class="sxs-lookup"><span data-stu-id="0a8ce-107">Better accuracy.</span></span>  
  
-   <span data-ttu-id="0a8ce-108">기능 추가</span><span class="sxs-lookup"><span data-stu-id="0a8ce-108">Added functionality.</span></span>  
  
 <span data-ttu-id="0a8ce-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장 프로시저에서 데이터를 반환 하는 데 사용 하는 세 가지 메커니즘을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports three of the mechanisms that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures use to return data:</span></span>  
  
-   <span data-ttu-id="0a8ce-110">프로시저의 모든 SELECT 문은 결과 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-110">Every SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="0a8ce-111">프로시저는 출력 매개 변수를 통해 데이터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-111">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="0a8ce-112">프로시저에는 정수 반환 코드가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-112">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="0a8ce-113">애플리케이션은 저장 프로시저의 이러한 모든 출력을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-113">The application must be able to handle all of these outputs from stored procedures.</span></span>  
  
 <span data-ttu-id="0a8ce-114">OLE DB 공급자는 결과를 처리하는 동안 각각 다른 시기에 출력 매개 변수와 반환 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-114">Different OLE DB providers return output parameters and return values at different times during result processing.</span></span> <span data-ttu-id="0a8ce-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자의 경우 소비자가 저장 프로시저에서 반환 된 결과 집합을 검색 하거나 취소할 때까지 출력 매개 변수 및 반환 코드가 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-115">In case of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the output parameters and return codes are not supplied until after the consumer has retrieved or canceled the result sets returned by the stored procedure.</span></span> <span data-ttu-id="0a8ce-116">반환 코드와 출력 매개 변수는 서버에서 보내는 마지막 TDS 패킷에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-116">The return codes and the output parameters are returned in the last TDS packet from the server.</span></span>  
  
 <span data-ttu-id="0a8ce-117">공급자는 출력 매개 변수와 반환 값을 반환할 때 DBPROP_OUTPUTPARAMETERAVAILABILITY 속성을 사용하여 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-117">Providers use the DBPROP_OUTPUTPARAMETERAVAILABILITY property to report when it returns output parameters and return values.</span></span> <span data-ttu-id="0a8ce-118">이 속성은 DBPROPSET_DATASOURCEINFO 속성 집합에 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-118">This property is in the DBPROPSET_DATASOURCEINFO property set.</span></span>  
  
 <span data-ttu-id="0a8ce-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자는 DBPROP_OUTPUTPARAMETERAVAILABILITY 속성을 DBPROPVAL_OA_ATROWRELEASE로 설정 하 여 반환 코드와 출력 매개 변수가 반환 되지 않고 결과 집합이 처리 되거나 해제 될 때까지 반환 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a8ce-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets the DBPROP_OUTPUTPARAMETERAVAILABILITY property to DBPROPVAL_OA_ATROWRELEASE to indicate that return codes and output parameters are not returned until the result set is processed or released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8ce-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a8ce-120">See Also</span></span>  
 [<span data-ttu-id="0a8ce-121">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="0a8ce-121">Stored Procedures</span></span>](stored-procedures.md)  
  
  
