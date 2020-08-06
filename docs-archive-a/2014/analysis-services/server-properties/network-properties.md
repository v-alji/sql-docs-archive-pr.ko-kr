---
title: 네트워크 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10ad5bbbcffdfc3d3c4fefe3111e4c4425919915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650305"
---
# <a name="network-properties"></a><span data-ttu-id="1bb09-102">네트워크 속성</span><span class="sxs-lookup"><span data-stu-id="1bb09-102">Network Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="1bb09-103">에서는 다음 표에 나열된 서버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="1bb09-104">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bb09-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="1bb09-105">**적용 대상:** 다차원 및 테이블 형식 서버 모드</span><span class="sxs-lookup"><span data-stu-id="1bb09-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="general"></a><span data-ttu-id="1bb09-106">일반</span><span class="sxs-lookup"><span data-stu-id="1bb09-106">General</span></span>  
 `ListenOnlyOnLocalConnections`  
 <span data-ttu-id="1bb09-107">로컬 연결(예: localhost)만 수신하는지 여부를 식별하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-107">A Boolean property that identifies whether to listen only on local connections, for example localhost.</span></span>  
  
## <a name="listener"></a><span data-ttu-id="1bb09-108">수신기</span><span class="sxs-lookup"><span data-stu-id="1bb09-108">Listener</span></span>  
 `IPV4Support`  
 <span data-ttu-id="1bb09-109">IPv4 프로토콜에 대한 지원을 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-109">A signed 32-bit integer property that defines support for IPv4 protocol.</span></span> <span data-ttu-id="1bb09-110">이 속성은 다음 표에 나열된 값 중 하나를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-110">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="1bb09-111">값</span><span class="sxs-lookup"><span data-stu-id="1bb09-111">Value</span></span>|<span data-ttu-id="1bb09-112">Description</span><span class="sxs-lookup"><span data-stu-id="1bb09-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1bb09-113">*0*</span><span class="sxs-lookup"><span data-stu-id="1bb09-113">*0*</span></span>|<span data-ttu-id="1bb09-114">IPv4가 해제되어 클라이언트가 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-114">IPv4 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="1bb09-115">*1*</span><span class="sxs-lookup"><span data-stu-id="1bb09-115">*1*</span></span>|<span data-ttu-id="1bb09-116">(기본값) IPv4가 필요하고 IPv4를 수신할 수 없으면 서버가 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-116">(Default) IPv4 is required; server won't start if it cannot listen to IPv4.</span></span>|  
|<span data-ttu-id="1bb09-117">*2*</span><span class="sxs-lookup"><span data-stu-id="1bb09-117">*2*</span></span>|<span data-ttu-id="1bb09-118">IPv4가 옵션이고 서버가 IPv4로 수신을 시도하기는 하지만 불가능한 경우에도 서버가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-118">IPv4 is optional; server tries to listen to IPv4 but starts even if unable to.</span></span>|  
  
 `IPV6Support`  
 <span data-ttu-id="1bb09-119">IPv6 프로토콜에 대한 지원을 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-119">A signed 32-bit integer property that defines support for IPv6 protocol.</span></span> <span data-ttu-id="1bb09-120">이 속성은 다음 표에 나열된 값 중 하나를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-120">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="1bb09-121">값</span><span class="sxs-lookup"><span data-stu-id="1bb09-121">Value</span></span>|<span data-ttu-id="1bb09-122">Description</span><span class="sxs-lookup"><span data-stu-id="1bb09-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1bb09-123">*0*</span><span class="sxs-lookup"><span data-stu-id="1bb09-123">*0*</span></span>|<span data-ttu-id="1bb09-124">IPv6이 해제되어 클라이언트가 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-124">IPv6 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="1bb09-125">*1*</span><span class="sxs-lookup"><span data-stu-id="1bb09-125">*1*</span></span>|<span data-ttu-id="1bb09-126">(기본값) IPv6이 필요하고 IPv6을 수신할 수 없으면 서버가 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-126">(Default) IPv6 is required; server won't start if it cannot listen to IPv6.</span></span>|  
|<span data-ttu-id="1bb09-127">*2*</span><span class="sxs-lookup"><span data-stu-id="1bb09-127">*2*</span></span>|<span data-ttu-id="1bb09-128">IPv6이 옵션이고 서버가 IPv6으로 수신을 시도하기는 하지만 불가능한 경우에도 서버가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-128">IPv6 is optional; server tries to listen to IPv6 but starts even if unable to.</span></span>|  
  
 `MaxAllowedRequestSize`  
 <span data-ttu-id="1bb09-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RequestSizeThreshold`  
 <span data-ttu-id="1bb09-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-130">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerReceiveTimeout`  
 <span data-ttu-id="1bb09-131">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-131">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerSendTimeout`  
 <span data-ttu-id="1bb09-132">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="requests"></a><span data-ttu-id="1bb09-133">요청</span><span class="sxs-lookup"><span data-stu-id="1bb09-133">Requests</span></span>  
 `EnableBinaryXML`  
 <span data-ttu-id="1bb09-134">서버에서 이진 xml 형식 요청을 식별하는지 여부를 지정하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-134">A Boolean property that specifies whether the server will recognize requests binary xml format.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="1bb09-135">요청에 대해 압축이 설정되어 있는지 여부를 지정하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-135">A Boolean property that specifies whether compression is enabled for requests.</span></span>  
  
## <a name="responses"></a><span data-ttu-id="1bb09-136">응답</span><span class="sxs-lookup"><span data-stu-id="1bb09-136">Responses</span></span>  
 `CompressionLevel`  
 <span data-ttu-id="1bb09-137">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-137">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `EnableBinaryXML`  
 <span data-ttu-id="1bb09-138">이진 xml 응답에 대해 서버가 설정되어 있는지 여부를 지정하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-138">A Boolean property that specifies whether the server is enabled for binary xml responses.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="1bb09-139">클라이언트 요청에 대한 응답으로 압축이 설정되어 있는지 여부를 지정하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-139">A Boolean property that specifies whether compression is enabled for responses to client requests.</span></span>  
  
## <a name="tcp"></a><span data-ttu-id="1bb09-140">TCP</span><span class="sxs-lookup"><span data-stu-id="1bb09-140">TCP</span></span>  
 `InitialConnectTimeout`  
 <span data-ttu-id="1bb09-141">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxCompletedReceiveCount`  
 <span data-ttu-id="1bb09-142">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingAcceptExCount`  
 <span data-ttu-id="1bb09-143">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingReceiveCount`  
 <span data-ttu-id="1bb09-144">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingSendCount`  
 <span data-ttu-id="1bb09-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-145">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingAcceptExCount`  
 <span data-ttu-id="1bb09-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingReceiveCount`  
 <span data-ttu-id="1bb09-147">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ScatterReceiveMultiplier`  
 <span data-ttu-id="1bb09-148">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ DisableNonblockingMode`  
 <span data-ttu-id="1bb09-149">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ EnableLingerOnClose`  
 <span data-ttu-id="1bb09-150">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\EnableNagleAlgorithm`  
 <span data-ttu-id="1bb09-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ LingerTimeout`  
 <span data-ttu-id="1bb09-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ ReceiveBufferSize`  
 <span data-ttu-id="1bb09-153">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-153">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ SendBufferSize`  
 <span data-ttu-id="1bb09-154">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1bb09-154">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb09-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bb09-155">See Also</span></span>  
 <span data-ttu-id="1bb09-156">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1bb09-156">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="1bb09-157">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="1bb09-157">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
