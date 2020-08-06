---
title: GetCurrentCertificate 메서드 (SInstance 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47838190e3791e01f8482e3fb064a9dca3a764af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661562"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="9c48c-102">GetCurrentCertificate 메서드(SInstance 클래스)</span><span class="sxs-lookup"><span data-stu-id="9c48c-102">GetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="9c48c-103">현재 보안 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c48c-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c48c-104">구문</span><span class="sxs-lookup"><span data-stu-id="9c48c-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="9c48c-105">부분</span><span class="sxs-lookup"><span data-stu-id="9c48c-105">Parts</span></span>  
 <span data-ttu-id="9c48c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9c48c-106">*object*</span></span>  
 <span data-ttu-id="9c48c-107">[인스턴스의 서버 설정을 나타내는](sinstance-class.md) SInstance 클래스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9c48c-107">An [SInstance Class](sinstance-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9c48c-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9c48c-108">Parameters</span></span>  
  
|<span data-ttu-id="9c48c-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9c48c-109">Parameter</span></span>|<span data-ttu-id="9c48c-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c48c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c48c-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="9c48c-111">*SHA*</span></span>|<span data-ttu-id="9c48c-112">메서드가 완료된 후 현재 보안 인증서를 지정하는 문자열 개체 값(출력 매개 변수)입니다.</span><span class="sxs-lookup"><span data-stu-id="9c48c-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9c48c-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="9c48c-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="9c48c-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9c48c-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c48c-115">설명</span><span class="sxs-lookup"><span data-stu-id="9c48c-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c48c-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c48c-116">See Also</span></span>  
 <span data-ttu-id="9c48c-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9c48c-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
