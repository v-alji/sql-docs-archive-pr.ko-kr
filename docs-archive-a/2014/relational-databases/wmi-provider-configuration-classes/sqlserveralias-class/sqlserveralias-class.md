---
title: SqlServerAlias 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46994409cc6a5119c9144eb7a3a4b9a8a9a22c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660936"
---
# <a name="sqlserveralias-class"></a><span data-ttu-id="73c9f-102">SqlServerAlias 클래스</span><span class="sxs-lookup"><span data-stu-id="73c9f-102">SqlServerAlias Class</span></span>
  <span data-ttu-id="73c9f-103">[SqlServerAlias 클래스](sqlserveralias-class.md) 는 서버 연결 별칭을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73c9f-103">The [SqlServerAlias Class](sqlserveralias-class.md) class represents a server connection alias.</span></span>  
  
 <span data-ttu-id="73c9f-104">서버 연결 별칭은 다음 두 가지 모두에 해당하는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="73c9f-104">A server connection alias is required when both the following occur:</span></span>  
  
-   <span data-ttu-id="73c9f-105">클라이언트가 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기본 네트워크 전송이 아닌 네트워크 전송을 통해 인스턴스에 연결 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73c9f-105">The client is connecting to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] over a network transport that is not the default network transport.</span></span>  
  
-   <span data-ttu-id="73c9f-106">클라이언트가 대체 명명된 파이프에서 수신하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 경우</span><span class="sxs-lookup"><span data-stu-id="73c9f-106">The instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the client is connected listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="73c9f-107">**참고:** [SqlServerAlias 클래스](sqlserveralias-class.md) 는 `Put` 공급자 클래스에서 메서드를 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c9f-107">**Note:** The [SqlServerAlias Class](sqlserveralias-class.md) inherits the `Put` method from the Provider class.</span></span> <span data-ttu-id="73c9f-108">`Provider::Put` 메서드가 표시하는 결과를 반환하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73c9f-108">However, it does not return any results as indicated by the `Provider::Put` method.</span></span> <span data-ttu-id="73c9f-109">자세한 내용은 WMI 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73c9f-109">For more information, see the WMI documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c9f-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73c9f-110">See Also</span></span>  
 [<span data-ttu-id="73c9f-111">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="73c9f-111">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
