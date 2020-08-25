<script>
const BASEURL="http://3.7.237.213:8080/"
export const API_LOGIN= BASEURL+"login";
export const API_CREATE_ROUTE = BASEURL+"routes";
export const API_SEARCH_RIDE = BASEURL+"rides/search?";
export const API_JOIN_RIDE = BASEURL+"ride-partners";
export const API_GET_UPCOMING_RIDE = BASEURL+"rides/upcoming?page=1&size=1000";
export const API_GET_COMPLETED_RIDE = BASEURL+"rides/completed?page=1&size=1000";
export const API_UPDATE_RIDE = BASEURL+"rides/";
export const API_CANCEL_RIDE_RIDE_PARTNER = BASEURL+"ride-partners/cancel/";
export const API_REGISTER_FOR_PUSH=BASEURL+"device/register";
export const API_DEREGISTER_FOR_PUSH=BASEURL+"device/deregister";
export const API_REFRESHTOKEN_FOR_PUSH=BASEURL+"device/refreshToken";
export const API_REGISTEREDDEVICES_FOR_PUSH=BASEURL+"device/my";
</script>
