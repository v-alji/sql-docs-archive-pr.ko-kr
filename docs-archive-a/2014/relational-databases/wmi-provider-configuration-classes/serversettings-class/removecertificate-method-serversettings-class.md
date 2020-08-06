---
title: RemoveCertificate 메서드 (ServerSettings 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00731fab5c4bdec61848df93829dd5013a7454f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729236"
---
# <a name="removecertificate-method-serversettings-class"></a><span data-ttu-id="8bd34-102">RemoveCertificate 메서드(ServerSettings 클래스)</span><span class="sxs-lookup"><span data-stu-id="8bd34-102">RemoveCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="8bd34-103">현재 보안 인증서를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8bd34-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd34-104">구문</span><span class="sxs-lookup"><span data-stu-id="8bd34-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="8bd34-105">부분</span><span class="sxs-lookup"><span data-stu-id="8bd34-105">Parts</span></span>  
 <span data-ttu-id="8bd34-106">*object*</span><span class="sxs-lookup"><span data-stu-id="8bd34-106">*object*</span></span>  
 <span data-ttu-id="8bd34-107">[인스턴스의 서버 설정을 나타내는](serversettings-class.md) ServerSettings 클래스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8bd34-107">A [ServerSettings Class](serversettings-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="8bd34-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="8bd34-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="8bd34-109">u`int32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8bd34-109">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd34-110">설명</span><span class="sxs-lookup"><span data-stu-id="8bd34-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd34-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bd34-111">See Also</span></span>  
 <span data-ttu-id="8bd34-112">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8bd34-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
